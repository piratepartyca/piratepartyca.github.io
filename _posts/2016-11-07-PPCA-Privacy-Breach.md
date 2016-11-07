---
title: Pirate Party Privacy Breach Notice
author: Travis McCrea
layout: post
categories: [internal]
---

> This is a notice to all old members of the Pirate Party who have used crm.pirateparty.ca / my.pirateparty.ca but have never signed into sso.pirateparty.ca. 

At 0200 PSDT (actually due to time paradox of DST I am not sure if this is 0200 PST or PDST), an email was sent to all older members of our party who had not yet signed into our new SSO system. An email was written to inform them of the new system and to request they update their information in our backend. Sadly, due to a bug in the script which emails out the members it iterated the list to each member who came after them in the database. 

IE Member 1 got their email then Member 1 got Member 2's email. Member 1 AND Member 2 then got Member 3s email. 

We tried to stop the emails from completing, as our email partner SendGrid has failsafes against this. Sadly by the time we got ahold of SendGrid the emails had already cleared the queue and we have no way of knowing how many of the 315 people who were on this list actually recieved the emails. What we do know is 4,072 were sent, and the code has already been updated so this problem never happens again. The damage, however, has been done and for a party that prides itself on personal privacy this breach is even worse.

### Technical Details

Our codebase is PHP, the code which caused the problem was a loop where the array wasn't reset between looping. This means for each additional member, instead of replacing the previous email, it added to it:

```
$sql = "SELECT email, name FROM users WHERE password = ''";
//$sql = "SELECT * FROM `users` WHERE `email` LIKE 'travis.mccrea@pirateparty.ca' ORDER BY `activateemail` DESC";

$result = mysqli_query($conn, $sql);
$json_string['category'] = 'welcomeemail';
if (mysqli_num_rows($result) > 0) {
    // output data of each row
    while($row = mysqli_fetch_assoc($result)) {
        $json_string['to'][] = $row["email"];
        $emailto = $row["email"];
        if($row['name'] == '') {
			$name='';
		} else {
			$name = ' '.$row['name'];
		}
		$textbody = "
Hello$name!

I try to keep emails to members a minimum but I wanted to ask that you come sign into our new member management system. As your account was rolled over from our old system you will need to create a new password. You can do that by using the password reset link below. Keeping an active account with the Pirate Party is just a tiny thing you can do to help us better organize and understand who our members are.

This may be the first time you are hearing from us in a long time, so let me just say we are rallying back after a few years of slacking. No more long meetings on insignificant internal bureaucratic policies, no more half baked projects that are not maintained, none of that. Just a simple website that tells you what we are about and better communication with the people who matter most (our members).  Welcome back to the Pirate Party! 

Reset your password: https://sso.pirateparty.ca/reset/$emailto

Thank you,

Travis McCrea - @TravisVancouver
Party Leader
604.500.4524 ";

//I have removed the CURL  as it didn't provide any help

    }
} else {
    echo "0 results";
}
```

This was purely sloppy coding, and it was my own fault. I had tested it, of course, but as you can see from my commented out test call it wasn't enough to show this problem. It was a problem that could only show in a test of multiple emails. 

### How To Prevent This

There are many ways this can be prevented in the future, the most obvious one is sleeping and coming back to things in the morning just to double check it. It seems like a lousy excuse and maybe a pointless step, but at least for me this is the hour where many of these issues start popping up so I am going to stick to it more closely.

On the technical side, I have added multiple accounts under a dummy name that no one else will have and emails will be tested against this list before others.

Also the proper code was put into place to reset the array. 

I am truly sorry to anyone who was affected by this, there is no action you need to take... no password information was shared (and our passwords are encrypted using B_CRYPT with 12 rounds of strength anyway). This information is here because I screwed up, and one of the things we do in the Pirate Party is admit our failures, we try not to spin them, and we move forward. So far the people who were up at this hour and have responded have seemed fairly understanding, I appreciate that and all I can do is promise to do better next time.

-- Travis McCrea
