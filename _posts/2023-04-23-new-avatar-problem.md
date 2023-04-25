---
title: Avatar Problems
date: 2023-04-23 12:01:00 -500
categories: [Jekyll, Blog]
tags: [blog,github,troubleshooting,jekyll,employers]     #TAG names should always be lowercase
---

<br>

>“All parts should go together without forcing.  You must remember that the parts you are reassembling were disassembled by you.  Therefore, if you can’t get them together again, there must be a reason.  By all means, do not use a hammer.”
— IBM Manual, 1925<br>- IBM Manual 1925

<br>

## How Do I Do That, Again?

I decided to change the avatar on the blog. The problem was, I hadn't messed with it in a while.

Nothing obvious jumped out while browsing the chirpy theme documentation. I did see lots of references to the *_config.yml* file. Looking at *_config.yml* in VSCode showed basic configuration options. The avatar option was here along with the URL for the old image. I replaced the URL with a link to the new picture, saved the file and committed the change to Github.

## Failed Build

While the Github Action ran I went and made some coffee. When I got back I saw the action failed failed.

<img src="https://i.imgur.com/bySDGS6.png" alt="Github Action Failed" width="100%" />

The details showed the error had something to do with Ruby. I know nothing about Ruby. Luckily, the error was straightfoward and included a fix.

<img src="https://i.imgur.com/qUPKfGq.png" alt="Wrong Platform" width="100%" />

The error seemed to show the build wanting a particular platform specified, __x86_64-linux__. This needed to be added to a lockfile. I was only aware of one file that sounded relevant, *Gemfile.lock*. I found the relevant __platform__ section inside *Gemfile.lock* and saw the platform included in the error, __x64-mingw-ucrt__.

<img src="https://i.imgur.com/qUPKfGq.png" alt="Github Action Error" width="100%" />

The error gave a CLI command to add the missing platform to the file. I manually added __x86_64-linux__ on a new line in the *Gemfile.lock*, assuming this is what the CLI command was doing. Once the new platform had been added to the lockfile I made the commit and watched the action run.

<img src="https://i.imgur.com/EyZpj43.png" alt="Run Initiated" width="100%" />

So far so good.

<img src="https://i.imgur.com/blrE7U4.png" alt="Run Looks Good So Far" width="100%" />

But... the action failed again.

<img src="https://i.imgur.com/AgkO1GA.png" alt="Failed Again" width="100%" />

Now what?

<img src="https://i.imgur.com/r6VDaoJ.png" alt="New Error" width="100%" />

__Liquid Exception: undefined method 'tainted?'__. Huh? No idea. A quick Google search took me back to Github, specifically, an Issues page where someone was reporting a very similar error. Reading through the comments it turned out to be an incompatibility issue with Liquid 4.0.3 and Ruby 3.2.0.

<img src="https://i.imgur.com/0hHe71d.png" alt="Liquid And Ruby Incompatibility" width="100%" />

Someone recommended a fix, code to add to *Gemfile*. The code looks like it is forcing Liquid version 4.0.4 or greater. I opened up *Gemfile* and added the code to the bottom of as suggested.

<img src="https://i.imgur.com/EG2YYuE.png" alt="Forcing Liquid Version" width="100%">

Save. Comment. Commit. Watch.

<img src="https://i.imgur.com/e62wk8L.png" alt="Running Action Again" width="100%" />

The Action ran successfully!

<img src="https://i.imgur.com/bdr4DGD.png" alt="Successful Action Ran" width="100%" />

Phew, that was a lot of work to just change an avatar image. Time to check out the page and verify the new image is there.

<img src="https://i.imgur.com/HFufEf4.png" alt="Blank Avatar" width="50%" />

Still blank. Forced a page refresh, tried a different browser, etc. Still blank. Maybe it was the new CDN I switched to for the new image? Out of curiosity, I decided to try a direct link to the Jekyll logo.

<img src="https://i.imgur.com/ioBXHPK.png" alt="Jekyll Logo" width="100%" />

I then added the link to the *_config.yml* file.

<img src="https://i.imgur.com/fhvRYVE.png" alt="Link Added to _config.yml" width="100%" />

Save. Comment. Commit. Watch.

<img src="https://i.imgur.com/BqKBmvV.png" alt="New Avatar Test Worked" width="50%" />

Okay so the direct link worked. I decided to upload my avatar to [Imgur](www.imgur.com) this time.

Save. Comment. Commit. Watch.

<img src="https://i.imgur.com/Qv6Jxob.png" alt="New Avatar Working" width="50%" />

Finally. Success.

## Conclusion

I concluded that something wonky was going on with the new CDN I had switched to. To verify, I saved and then uploaded the same Jekyll image to the new CDN, made the change in the _config.yml, commented, committed and checked the site. Blank avatar. Hosting the image on Imgur(www.imgur.com) resolved the issue.
