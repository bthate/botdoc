.. _home:


.. raw:: html

  <br>


.. title:: python3 bot library


**NAME**


 **BOTLIB** - python3 bot library 


**SYNOPSIS**


  | ``bot [cmd] [-c] [-i] [key=value] [key==value]``


**INSTALL**


 ``pip3 install botlib --upgrade --force-reinstall``

**DESCRIPTION**


 **BOTLIB** is a solid, non hackable bot, that runs under systemd as a 24/7
 background service and starts the bot after reboot, intended to be
 programmable in a static, only code, no popen, no imports and no reading
 modules from a directory,  source is :ref:`here <source>`.

 **BOTLIB** is programmable, to program the bot you have to have the code
 available as employing your own code requires that you install your own bot as
 the system bot. This is to not have a directory to read modules from to add
 commands to the bot but include the own programmed modules directly into the
 python code, so only trusted code (your own written code) is included and
 runnable. Reading random code from a directory is what gets avoided.

 **BOTLIB** stores it's data on disk where objects are time versioned and the
 last version saved on disk is served to the user layer. Files are JSON dumps
 that are read-only so thus should provide (disk) persistence more chance.
 Paths carry the type in the path name what makes reconstruction from filename
 easier then reading type from the object.

 only include your own written code should be the path to "secure".


**CONFIGURATION**

 configuration is done by calling the ``cfg`` command of the bot.

 **irc**

 | ``bot cfg server=<server> channel=<channel> nick=<nick>``

 | (*) default channel/server is #botd on localhost

 **sasl**

 | ``bot pwd <nickservnick> <nickservpass>``
 | ``bot cfg password=<outputfrompwd>``

 **users**

 | ``bot cfg users=True``
 | ``bot met <userhost>``


 **rss**

 | ``bot rss <url>``
 |

**SYSTEMD**

 to run the bot after reboot, install the service file and start the service
 by enabling it with ``--now``.

 | $ ``sudo cp /usr/local/share/botd/botd.service /etc/systemd/system``
 | $ ``sudo systemctl enable botd --now``

 | (*) default channel/server is #botd on localhost

 use ``botctl`` instead of the use ``bot`` program

 | $ ``sudo botctl cfg server=<server> channel=<channel> nick=<nick>``
 | $ ``sudo botctl pwd <nickservnick> <nickservpass>``
 | $ ``sudo botctl cfg password=<outputfrompwd>``
 | $ ``sudo botctl cfg users=True``
 | $ ``sudo botctl met <userhost>``
 | $ ``sudo botctl rss <url>``
 |

**RUNNING**

 run the bot with the ``bot`` command, it will start a shell with
 the irc bot. use the -c option if you don't want just the console.
 you can also run the bot as a cli, directly giving a command.

 | ``bot [cmd] [-c] [-i]``

 **cli**

 without any arguments the bot will not react.

 | ``$ bot``
 | ``$``

 when giving an argument it will run that command.

 | ``$ bot cmd``
 | ``cfg,cmd,dlt,flt,fnd,met,mre,pwd,thr``
 |

 **console**

 | ``$ bot -c``
 | ``BOT start at Fri Apr 1 20:02:40 2022``
 | ``> thr``
 | ``Console.loop/1s``
 | ``>`` 

 **irc**

 | ``$ bot -i``
 | ``BOT start at Fri Apr 1 20:00:43 2022``
 | ``server=localhost port=6667 channel=#botd nick=botlib cc=!``
 | ``> thr``
 | ``Console.loop/1s IRC.keep/1s IRC.loop/1s IRC.output/1s Fetcher.run/4m59s``
 | ``>`` 
 |

**COMMANDS**

 here is a short description of the commands.

 | ``cmd`` - shows all commands
 | ``cfg`` - shows the irc configuration, also edits the config
 | ``dlt`` - removes a user from bot
 | ``dpl`` - sets display items for a rss feed
 | ``ftc`` - runs a rss feed fetching batch
 | ``fnd`` - allows you to display objects on the datastore, read-only json files on disk 
 | ``flt`` - shows a list of bot registered to the bus
 | ``log`` - logs some text
 | ``met`` - adds a users with there irc userhost
 | ``mre`` - displays cached output, channel wise.
 | ``nck`` - changes nick on irc
 | ``pwd`` - combines a nickserv name/password into a sasl password
 | ``rem`` - removes a rss feed by matching is to its url
 | ``rss`` - adds a feed to fetch, fetcher runs every 5 minutes
 | ``thr`` - show the running threads
 | ``tdo`` - adds a todo item, no options returns list of todo's
 |

**AUTHOR**

 Bart Thate

**COPYRIGHT**

 **BOTLIB** is placed in the Public Domain. No Copyright, No License.


.. toctree::
    :hidden:
    :glob:

    *
