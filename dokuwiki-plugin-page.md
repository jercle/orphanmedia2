====== OrphanMedia2 Plugin ======

---- plugin ----
description: Display orphan and missing media files. Based on unmaintained orphanmedia plugin
author     : jercle
email      : ercolwell@gmail.com
type       : syntax
lastupdate : 2023-02-15
compatible : anteater, rincewind, angua, "Adora Belle", Elenor Of Tsort, Frusterick Manners, Greebo, Hogfather, Igor
depends    :
conflicts  :
similar    : OrphansWanted,MultiOrphan,orphanmedia
tags       : orphan, maintenance, links, listing, search, missing

downloadurl: http://github.com/jercle/orphanmedia2/zipball/master
bugtracker : http://github.com/jercle/orphanmedia2/issues
sourcerepo : http://github.com/jercle/orphanmedia2/
----

Based on the abandoned [[https://www.dokuwiki.org/plugin:orphanmedia|OrphanMedia Plugin]]

===== Installation =====
Search and install the plugin using the [[plugin:extension|Extension Manager]]. Refer to [[:Plugins]] on how to install plugins manually.

==== Changes ====

{{rss>https://github.com/jercle/orphanmedia2/commits/main.atom date}}

===== Examples/Usage =====
Use this plugin to find orphan and missing media files within your DokuWiki. There are 4 options provided to get the related information.

OrphanMedia show which medias are:
^ Option  ^ Output  ^
| all  | will display the complete set of results of the other parameters togethers  |
| summary  | __Counter based information:__ \\ # of Page files \\  # of Media files \\  # of Media references \\  -> Filter settings \\  # of valid, qualified references \\  # of valid, relative references \\  # of Missing media files \\  # of Orphan media files  |
| valid | all valid media links referenced by full qualified path will be displayed  |
| relative | all valid media links referenced by relative path will be displayed  |
| missing | Missing Media, the media file does not exist, but there are link(s) to it elsewhere on the pages  |
| orphan  | Orphan Media, the media file exists, but not linked and wasting space only  |

===== Detection & Limits =====
^  Link Type  ^  Comment  ^
| standard, local DW media links \\ <nowiki>{{:ns:mediafile|title}}</nowiki>  | full qualified links also as relative links, with or without parameters, all detected  |
| enclosed DW media links \\ <nowiki><box params|{{:ns:mediafile|title}}></nowiki> | all detected  |
| specials excluded | medialinks within %%<code>, <file>, <nowiki>, <php>, <html> and %%%% are ignored \\ further can be excluded by adding regexpr to plugin conf  |
| linked external media files \\ <nowiki>{{http://www.wherever.com/whatsoever.type}}</nowiki>  | all detected; if valid, they will be viewed within relative section. \\ __**Attention:**__ \\ mediafile will be displayed as missing in the event a login will be neccesary to open it \\ (e.g. linked documents from CMS)  |
| gallery plugin references \\ <nowiki>{{gallery ...</nowiki>  | not recognized, will be displayed as orphan if not otherwise linked  |
| flashplayer  | flashplayer may work for local files (not yet tested sufficiently)  |
| unc path  | not yet tested sufficiently  |
| windows shares  | not yet tested sufficiently  |
===== Syntax =====
**Basic** usage is to place one of the following five syntax lines into the page markup of a page with Admin/Superuser ACL:
<code>
 ====== Orphan Media detection ======
  ~~NOCACHE~~
  ~~ORPHANMEDIA:all~~
  ~~ORPHANMEDIA:summary~~
  ~~ORPHANMEDIA:valid~~
  ~~ORPHANMEDIA:relative~~
  ~~ORPHANMEDIA:missing~~
  ~~ORPHANMEDIA:orphan~~
</code>

The summary will be displayed in any case.

You can combine outputs. For instance you want to see the summary, missing and orphan option only \\
the following syntax is valid (put the options together without delimiter):
  ~~ORPHANMEDIA:missingorphan~~
Further you can specify a filter to limit the output to then specified file-extension according \\
following example (add file-extensions separated by ":"):
  ~~ORPHANMEDIA:all:png:jpg:gif~~
:!: The summary counters will be affected accordingly beside the limited output.

It does also check for flashplayer-plugin links if they refer to local path.
===== Development =====

Each valuable help is welcome. The code is not that complicated, just looping through and \\
displaying some filename and path info without any effect to your source.


===== Version/Requirements =====
The plugin was tested with DW 2022-07-31 "Igor" and older.

=== Weakpoint ===
If you have multiple pictures named e.g. //Image006.gif// then the tool fails. \\
Please try to keep good style by authoring and give descriptive names to your media files.

=== Known Bugs and Issues ===
It could happen that not all media files will be detected or some feed links, etc. interpreted as such. \\
I tried to filter that out but due to that many syntax plugins it cannot catch all issues. \\
If  you have a real problem please tell me the root cause of your problem at:
[[http://github.com/jercle/orphanmedia2/issues|OrphanMedia2 Issues]]

===== Sites using this Plugin =====
Feel free to add yours here:
  *

===== Discussion and Bugs =====
Please use only the DokuWiki Forum for discussion. To report an issue please refer to:
[[http://github.com/jercle/orphanmedia2/issues|OrphanMedia2 Issues]]
