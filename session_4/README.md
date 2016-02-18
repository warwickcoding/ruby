| [← Session 3](../session_3/README.md) |
|---------------------------------------|

##Ruby Course Session 4

Session Outline:
- Recap
- Upgrading our Ruby version
- Arrays
- Hashes
- Exercises



Recap of Session 3
------------------
In the previous session, we got introduces to different loops in the Ruby language. We started with `while` loops and demonstrated how they perform. We then moved onto `for`, `upto`, `downto`, and `times` loops. We saw how each of them work and how some of them can be used in lieu of others.



Upgrading our Ruby version
--------------------------
As you might remember from the first session, we installed Ruby 2.0.0 using Koding's built in package manager. That was fine for the first few sessions because we were learning about some core features of Ruby that have not changed much since that version. Today, the latest stable release of Ruby is 2.3.0, this is something that we can check out from the [Ruby-lang website](https://www.ruby-lang.org/en/downloads/).

In order to download different versions of Ruby, we will be using a version manager to that, called [RVM](https://rvm.io/). RVM allows us to easily install, manage, and work with multiple ruby environments from interpreters to sets of gems. Please feel free to read more about RVM on its website.

Please follow the below instructions carefully and don't make any spelling mistakes. Also, when you see the word `username` this means you have to replace it with your actual username which is first word that shows up when you fire up your terminal, before the `:`. For example, here is mine:
![img1](../images/session_4/ruby_session_4-1.png)

1. Open up a Terminal tab and type: `sudo chown -R username ~username/.gnupg`
2. Type `chmod 600 ~/.gnupg/gpg.conf`
3. Type `chmod 700 ~/.gnupg`
4. Go to https://rvm.io/rvm/install
5. Copy the entire command that begins with `gpg` into your terminal
6. Then type the following into your terminal: `\curl -sSL https://get.rvm.io | bash -s stable --ruby`

If you followed the above steps, you should now be able to use rvm as your version manager for different Ruby versions. The first thing we are going to do it to use the latest stable release and make it the default version.

- Type `rvm install 2.3.0` into your terminal and wait for it to install
- As soon as the download is complete, type `rvm list'. We are looking for that new version to be in our list. 
- If you see the version, please type `rvm use 2.3.0 --default`, which will now make our default version of Ruby to 2.3.
- To confirm that this is the case, please type `ruby -v` and expect to see that new version




