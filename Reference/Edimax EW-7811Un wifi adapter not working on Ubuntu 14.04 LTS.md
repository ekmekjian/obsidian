---
_Source URL: [](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts)._

---

# Edimax EW-7811Un wifi adapter not working on Ubuntu 14.04 LTS


<https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#>

2.  <https://stackexchange.com/users/?tab=inbox>
3.  <https://stackexchange.com/users/?tab=reputation>
4.  <https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#>
5.  <https://stackexchange.com/>
6.  [Log In](https://askubuntu.com/users/login?ssrc=head&returnurl=https%3a%2f%2faskubuntu.com%2fquestions%2f612649%2fedimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts) [Sign Up](https://askubuntu.com/users/signup?ssrc=head&returnurl=https%3a%2f%2faskubuntu.com%2fquestions%2f612649%2fedimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts)

By using our site, you acknowledge that you have read and understand our [Cookie Policy](https://stackoverflow.com/legal/cookie-policy), [Privacy Policy](https://stackoverflow.com/legal/privacy-policy), and our [Terms of Service](https://stackoverflow.com/legal/terms-of-service/public).

<https://askubuntu.com/>![[logo.svg]]

Ask Ubuntu is a question and answer site for Ubuntu users and developers. Join them; it only takes a minute:
[Sign up](https://askubuntu.com/users/signup?ssrc=hero&returnurl=https%3a%2f%2faskubuntu.com%2fquestions%2f612649%2fedimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts)

Here's how it works:

Anybody can ask a question

Anybody can answer

The best answers are voted up and rise to the top

3.  [Home](https://askubuntu.com/)
    2.  [Questions](https://askubuntu.com/questions)
    3.  [Tags](https://askubuntu.com/tags)
    4.  [Users](https://askubuntu.com/users)
    5.  [Unanswered](https://askubuntu.com/unanswered)
    

# [Edimax EW-7811Un wifi adapter not working on Ubuntu 14.04 LTS](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts)

[Ask Question](https://askubuntu.com/questions/ask)

 2  [favorite](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)
**2**

I have installed Ubuntu 14.04 LTS 64-Bit and have a Edimax EW-7811Un wifi adapter. I have tired to get it to work but have no luck.

when I run lsusb command I get:

`Bus 001 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]` 

iwconfig shows that nothing is being read or connected:

`eth0      no wireless extensions.
lo        no wireless extensions.` 

I have tired numerous forums and tutorials but cant get it to work, dont know what I am doing wrong.

Can someone give a clear step by step method to get this to work?

uname -r: (Kernel Version)

`3.16.0-34-generic` 

[14.04](https://askubuntu.com/questions/tagged/14.04) [wireless](https://askubuntu.com/questions/tagged/wireless) [drivers](https://askubuntu.com/questions/tagged/drivers) [adapter](https://askubuntu.com/questions/tagged/adapter)

[share](https://askubuntu.com/q/612649)|[improve this question](https://askubuntu.com/posts/612649/edit)

asked Apr 22 '15 at 22:17
[![[eca6067f5a7dc169ebbc772c3d199a2b.png]]](https://askubuntu.com/users/397503/harnamc)
[Harnamc](https://askubuntu.com/users/397503/harnamc)
**60**118

## 2 Answers

[active](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts?answertab=active#tab-top) [oldest](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts?answertab=oldest#tab-top) [votes](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts?answertab=votes#tab-top)

 6  accepted

This has been reported to work:

`sudo apt-get install linux-headers-generic build-essential dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
sudo depmod -a
sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/` 

Reboot

([Source](https://github.com/pvaret/rtl8192cu-fixes#installation))

[share](https://askubuntu.com/a/612651)|[improve this answer](https://askubuntu.com/posts/612651/edit)

[edited Feb 10 '16 at 9:44](https://askubuntu.com/posts/612651/revisions)
[![[E0SEH.png]]](https://askubuntu.com/users/175814/david-foerster)
[David Foerster](https://askubuntu.com/users/175814/david-foerster)
**26.7k**1363106

answered Apr 22 '15 at 22:27
[![[407bbdcca9081760084730b2b3e229b8.png]]](https://askubuntu.com/users/300665/jeremy31)
[Jeremy31](https://askubuntu.com/users/300665/jeremy31)
**8,030**21361

*   PERFECT!!! Thank you mate, been searching long and hard for this. – [Harnamc](https://askubuntu.com/users/397503/harnamc) [Apr 22 '15 at 22:34](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#comment862400_612651)
    
*   Should I be worried about all the failed attempts and random drivers I have tried to download and install? Is there a way to clean/flush them? – [Harnamc](https://askubuntu.com/users/397503/harnamc) [Apr 22 '15 at 22:36](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#comment862402_612651)
    
*   This likely replaced all that since it worked – [Jeremy31](https://askubuntu.com/users/300665/jeremy31) [Apr 22 '15 at 23:12](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#comment862420_612651)
    
*   Under Ubuntu 14.04 LTS the adaptor seems to be supported but the connection is intermittent. For anyone facing this problem while applying this patch, I recommend just disconnecting and re-connecting to the Wifi hotspot. – [Andy J](https://askubuntu.com/users/55321/andy-j) [Jan 3 '16 at 5:56](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#comment1057053_612651)
    
*   how do we undo this - i did this and found that it did not support 5GHz. My internal realtek8723be works just fine too (i manually built and installed rtlwifi\_new). So i want to go back to that. Presently after this, when i take out the edimax usb, i dont even get the enable-wifi listed. So how to undo this ? – [ustulation](https://askubuntu.com/users/542532/ustulation) [May 19 '16 at 18:14](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#comment1158056_612651)
    

 0 

Ubuntu makes newer kernels (and X Windows) available to the LTS releases, called the [LTS Enablement Stack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack). I installed the latest kernel on my 14.04 (Trusty) system, which at the time of writing is the kernel for Xenial (16.04). Newer kernels have newer drivers and firmware.

`sudo apt-get install --install-recommends linux-generic-lts-xenial` 

Then reboot to upgrade to the Xenial kernel. On my system, the Edimax adapter worked fine afterward.

[share](https://askubuntu.com/a/830850)|[improve this answer](https://askubuntu.com/posts/830850/edit)

answered Sep 28 '16 at 17:47
[![[d67b41634de434e174b10901c9fa45e6.jpg]]](https://askubuntu.com/users/209764/ethan-t)
[Ethan T](https://askubuntu.com/users/209764/ethan-t)
**108**5

## Your Answer

### Sign up or [log in](https://askubuntu.com/users/login?ssrc=question_page&returnurl=https%3a%2f%2faskubuntu.com%2fquestions%2f612649%2fedimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts%23new-answer)

Sign up using Google
Sign up using Facebook
Sign up using Email and Password

### Post as a guest

**Name**
**Email**

By clicking "Post Your Answer", you acknowledge that you have read our updated [terms of service](https://stackoverflow.com/legal/terms-of-service/public), [privacy policy](https://stackoverflow.com/legal/privacy-policy) and [cookie policy](https://stackoverflow.com/legal/cookie-policy), and that your continued use of the website is subject to these policies.

## Not the answer you're looking for? Browse other questions tagged [14.04](https://askubuntu.com/questions/tagged/14.04) [wireless](https://askubuntu.com/questions/tagged/wireless) [drivers](https://askubuntu.com/questions/tagged/drivers) [adapter](https://askubuntu.com/questions/tagged/adapter) or [ask your own question](https://askubuntu.com/questions/ask).

|     |     |
| --- | --- |
| asked | **3 years, 5 months ago** |
| viewed | **12,408 times** |
| active | **[2 years ago](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts?lastactivity)** |

#### Linked

[0](https://askubuntu.com/q/731750?lq=1)[Slow wifi in ubuntu 14.04 with realtek wifi adapter](https://askubuntu.com/questions/731750/slow-wifi-in-ubuntu-14-04-with-realtek-wifi-adapter?noredirect=1&lq=1)
[0](https://askubuntu.com/q/724699?lq=1)[How to make WiFi adapter EW-7811UN running on 14.04 Ubuntu](https://askubuntu.com/questions/724699/how-to-make-wifi-adapter-ew-7811un-running-on-14-04-ubuntu?noredirect=1&lq=1)

#### Related

[0](https://askubuntu.com/q/91656?rq=1)[Edimax EW-7811Un USB Wirless Adapter Stopped Working](https://askubuntu.com/questions/91656/edimax-ew-7811un-usb-wirless-adapter-stopped-working?rq=1)
[0](https://askubuntu.com/q/223026?rq=1)[How do I get wireless usb adapter TL-WN727N working in 12.04?](https://askubuntu.com/questions/223026/how-do-i-get-wireless-usb-adapter-tl-wn727n-working-in-12-04?rq=1)
[0](https://askubuntu.com/q/278588?rq=1)[Wireless not work on Ubuntu 12.10 Realtek RTL8111/8168B](https://askubuntu.com/questions/278588/wireless-not-work-on-ubuntu-12-10-realtek-rtl8111-8168b?rq=1)
[2](https://askubuntu.com/q/372057?rq=1)[Edmiax Mini Wifi Dongle (RTL8188CUS) not working](https://askubuntu.com/questions/372057/edmiax-mini-wifi-dongle-rtl8188cus-not-working?rq=1)
[1](https://askubuntu.com/q/466559?rq=1)[Wireless is disabled by hardware switch. Wifi doesn't work! (hard blocked: yes,soft blocked :no, hp pavillion g6 2237, Ubuntu 12.04)?](https://askubuntu.com/questions/466559/wireless-is-disabled-by-hardware-switch-wifi-doesnt-work-hard-blocked-yes-s?rq=1)
[1](https://askubuntu.com/q/670288?rq=1)[WIFI USB adapter - Sitecom WLA-3001 AC450 instalation](https://askubuntu.com/questions/670288/wifi-usb-adapter-sitecom-wla-3001-ac450-instalation?rq=1)
[2](https://askubuntu.com/q/820411?rq=1)[How can I fix frequent connection drops of my WiFi?](https://askubuntu.com/questions/820411/how-can-i-fix-frequent-connection-drops-of-my-wifi?rq=1)
[4](https://askubuntu.com/q/929870?rq=1)[Wifi suddenly going off periodically](https://askubuntu.com/questions/929870/wifi-suddenly-going-off-periodically?rq=1)
[1](https://askubuntu.com/q/1045149?rq=1)[Edimax EW-7811 UTC wireless usb adapter](https://askubuntu.com/questions/1045149/edimax-ew-7811-utc-wireless-usb-adapter?rq=1)
[1](https://askubuntu.com/q/1059738?rq=1)[ZTE Modem not working on Ubuntu 18.04](https://askubuntu.com/questions/1059738/zte-modem-not-working-on-ubuntu-18-04?rq=1)

#### [Hot Network Questions](https://stackexchange.com/questions?tab=hot)

*   [How can I, a high school student in Bucharest, go on to become an ISS astronaut?](https://space.stackexchange.com/questions/31259/how-can-i-a-high-school-student-in-bucharest-go-on-to-become-an-iss-astronaut)
*   [Credit debt now larger than mortgage](https://money.stackexchange.com/questions/100864/credit-debt-now-larger-than-mortgage)
*   [Why is the debate on the composition of the U.S. Supreme Court so politicised?](https://politics.stackexchange.com/questions/34257/why-is-the-debate-on-the-composition-of-the-u-s-supreme-court-so-politicised)
*   [Command line argument in awk](https://unix.stackexchange.com/questions/475008/command-line-argument-in-awk)
*   [Etiquette of playing musical instruments on popular hikes](https://outdoors.stackexchange.com/questions/20703/etiquette-of-playing-musical-instruments-on-popular-hikes)
*   [My 3 year old daughter thinks she is white. Should I tell her she's not?](https://parenting.stackexchange.com/questions/34988/my-3-year-old-daughter-thinks-she-is-white-should-i-tell-her-shes-not)
*   [What is Pathfinder's relationship to D&D?](https://rpg.stackexchange.com/questions/133423/what-is-pathfinders-relationship-to-dd)
*   [Is this minesweeper board inconsistent?](https://gaming.stackexchange.com/questions/339539/is-this-minesweeper-board-inconsistent)
*   [why don't I want to learn anything?](https://academia.stackexchange.com/questions/118266/why-dont-i-want-to-learn-anything)
*   [How can I initiate a talk of money with my friend about his business idea?](https://interpersonal.stackexchange.com/questions/19248/how-can-i-initiate-a-talk-of-money-with-my-friend-about-his-business-idea)
*   [What would the proper shooting stance be for a recoil-free arm cannon?](https://worldbuilding.stackexchange.com/questions/127199/what-would-the-proper-shooting-stance-be-for-a-recoil-free-arm-cannon)
*   [How hard would it be to fly a Space Shuttle again?](https://space.stackexchange.com/questions/31281/how-hard-would-it-be-to-fly-a-space-shuttle-again)
*   [Output a 2D Array in an Anti-clockwise Fashion](https://codegolf.stackexchange.com/questions/173869/output-a-2d-array-in-an-anti-clockwise-fashion)
*   [DNS resolves wrong IP address in one country](https://serverfault.com/questions/935025/dns-resolves-wrong-ip-address-in-one-country)
*   [What is the dented wheel with holes inside the Polaroid Land Camera Model 150](https://photo.stackexchange.com/questions/102077/what-is-the-dented-wheel-with-holes-inside-the-polaroid-land-camera-model-150)
*   [Bash Script to remotely collect hostname, IP and host total memory](https://unix.stackexchange.com/questions/474996/bash-script-to-remotely-collect-hostname-ip-and-host-total-memory)
*   [Build an impregnable fortress in the middle ages with modern technology](https://worldbuilding.stackexchange.com/questions/127177/build-an-impregnable-fortress-in-the-middle-ages-with-modern-technology)
*   [How can I avoid problems that arise from rolling ability scores?](https://rpg.stackexchange.com/questions/133350/how-can-i-avoid-problems-that-arise-from-rolling-ability-scores)
*   [Just started a postdoc, but it went REALLY bad, REALLY fast. Stay or go?](https://academia.stackexchange.com/questions/118282/just-started-a-postdoc-but-it-went-really-bad-really-fast-stay-or-go)
*   [How to perform field update before a Validation Rule? (without code)](https://salesforce.stackexchange.com/questions/235764/how-to-perform-field-update-before-a-validation-rule-without-code)
*   [Pentomino 6x10 solution normalizer](https://codegolf.stackexchange.com/questions/173905/pentomino-6x10-solution-normalizer)
*   [Last computer not to use 8-bit bytes](https://retrocomputing.stackexchange.com/questions/7937/last-computer-not-to-use-8-bit-bytes)
*   [Who are the three men standing and what are they holding at this University of Paris Doctors' Meeting?](https://history.stackexchange.com/questions/48631/who-are-the-three-men-standing-and-what-are-they-holding-at-this-university-of-p)
*   [Is it a good practice to create a desktop shortcut on mac?](https://apple.stackexchange.com/questions/338917/is-it-a-good-practice-to-create-a-desktop-shortcut-on-mac)

[question feed](https://askubuntu.com/feeds/question/612649)

##### [Ask Ubuntu](https://askubuntu.com/)

*   [Tour](https://askubuntu.com/tour)
*   [Help](https://askubuntu.com/help)
*   [Chat](https://chat.stackexchange.com/?tab=site&host=askubuntu.com)
*   [Contact](https://askubuntu.com/contact)
*   [Feedback](https://meta.askubuntu.com/)
*   
*   

##### [Company](https://stackoverflow.com/company/about)

*   [Stack Overflow](https://stackoverflow.com/)
*   [Stack Overflow Business](https://www.stackoverflowbusiness.com/)
*   [Developer Jobs](https://stackoverflow.com/jobs)
*   [About](https://stackoverflow.com/company/about)
*   [Press](https://stackoverflow.com/company/press)
*   [Legal](https://stackoverflow.com/legal)
*   [Privacy Policy](https://stackoverflow.com/legal/privacy-policy)

##### [Stack Exchange
Network](https://stackexchange.com/)

*   [Technology](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)
*   [Life / Arts](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)
*   [Culture / Recreation](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)
*   [Science](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)
*   [Other](https://askubuntu.com/questions/612649/edimax-ew-7811un-wifi-adapter-not-working-on-ubuntu-14-04-lts#)

*   [Blog](https://stackoverflow.blog/?blb=1)
*   [Facebook](https://www.facebook.com/officialstackoverflow/)
*   [Twitter](https://twitter.com/stackoverflow)
*   [LinkedIn](https://linkedin.com/company/stack-overflow)

site design / logo © 2018 Stack Exchange Inc; user contributions licensed under [cc by-sa 3.0](https://creativecommons.org/licenses/by-sa/3.0/) with [attribution required](https://stackoverflow.blog/2009/06/25/attribution-required/). rev 2018.10.10.31893

Ubuntu and Canonical are registered trademarks of Canonical Ltd.

