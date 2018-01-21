I use OVH VPS for my leisure computing. Those are cheap, solid and comes with Arch Linux - the one that I prefer to use over any other distribution \(sorry Debian - you're my second choice\).

Keeping your system up-to-date is one of most important tasks. Here is how to do this:

> \[root@vps123456 ~\]\# pacman -Syu  
> \[root@vps123456 ~\]\# sync  
> \[root@vps123456 ~\]\# reboot

I tend to use Ansible to perform all VPS managament. Main reason why I spend so much time writing the Ansible recipes is to ensure that I can recreate my configurations any time. Easiest step to get Ansible up and running:

> \[root@vps123456 ~\]\# pacman -S ansible  
> \[root@vps502782 ~\]\# ansible --version  
> ansible 2.4.2.0

.

.

