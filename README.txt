SHULKER V2 FREE - SETUP GUIDE (LINUX)
======================================
thanks for downloading shulker v2 free. this guide covers everything you need
to get started on linux.

NOTE: this is the free version. some features from the premium version are not
included. see the "WHY PREMIUM?" section at the bottom, or visit
discord.gg/gU3BwPBvXb to upgrade.


USEFUL LINKS
------------
discord.gg/gU3BwPBvXb   - buy premium or get support
chat.shulkerV2.xyz      - contact us directly


QUICK START
-----------
1. make the binary executable:  chmod +x ShulkerV2
2. put your combos in combos.txt (format: email:password, one per line)
3. put proxies in proxies.txt if you have them (ip:port or ip:port:user:pass)
4. set up webhooks in webhook_config.json if you want discord notifications (optional)
5. run it:  ./ShulkerV2

no license key needed. just run it.


LINUX REQUIREMENTS
------------------
- any linux distro (ubuntu, debian, centos, arch, etc.)
- no dependencies needed, it is a single binary
- works on VPS, dedicated servers, and local machines
- tested on ubuntu 22.04/24.04 and debian 11/12


FILES
-----
  combos.txt            your account list to check
  proxies.txt           proxy list (optional but strongly recommended)
  config.ini            all settings
  webhook_config.json   discord webhook settings
  results/              created automatically, all your hit files go here


DISPLAY MODES
-------------
when you launch the checker it will ask you to pick a mode:

  logs mode  - shows every account being checked in real time with full output
  CUI mode   - clean dashboard with live totals and stats, no per-account noise
               recommended for large runs


CONFIG SETTINGS
---------------
all settings are in config.ini.

  [threads]
    mode                      auto or manual (auto = one thread per valid proxy)
    count                     number of threads, only used if mode = manual

  [proxy]
    mode                      sticky or rotating
    protocol                  http, socks4, or socks5
    file                      path to your proxy file (default: proxies.txt)
    validate                  true/false, validate sticky proxies on startup

  [features]
    hypixel_check             check hypixel ban status and stats
    ban_check                 minecraft ban detection
    xbox_perks                grab xbox perk and promo codes
    ms_rewards                check microsoft rewards points
    set_name                  auto rename accounts eligible for name changes
    set_skin                  auto set a skin on every account
    skin_url                  url of the skin image to use
    inbox_checker             check outlook inbox for keywords
    inbox_keywords            comma separated list of keywords to search for

  [naming]
    prefix                    text at the start of every name (e.g. Sv2)
    suffix                    optional text at the end (e.g. YT, or leave empty)
    separator                 character between parts (e.g. _, -, or none)
    use_words                 true/false, adds a random word (e.g. Wolf, Blade)
    words                     how many words to include (1 recommended)
    random_length             length of the random part (minimum 3)

  [input]
    combos                    path to your combos file (default: combos.txt)

  [display]
    show_invalid              show/hide invalid accounts in logs mode
    show_valid                show/hide valid accounts in logs mode
    show_hits                 show/hide MC/Xbox hits in logs mode
    show_locked               show/hide locked/2FA accounts in logs mode

  [output]
    create_results_folder     true/false, create a timestamped results folder
    save_by_category          true/false, save results into category subfiles

  [auto_run]
    enabled                   true/false, skip startup questions and launch directly
    proxy_protocol            http, socks4, or socks5
    proxy_mode                sticky or rotating
    display_mode              logs or cui
    threads                   0 = use [threads] settings, any number overrides


RESULT FILES
------------
a results folder is created automatically. files inside:

  all_hits.txt                  everything combined (minecraft + xbox)
  mc_hits.txt                   minecraft java accounts
  mc_capture.txt                minecraft accounts with username and ban status
  mctoken.txt                   minecraft account tokens
  ms_valid.txt                  valid microsoft accounts (no minecraft)
  xbox_game_pass.txt            accounts with xbox game pass
  xbox_game_pass_ultimate.txt   accounts with xbox game pass ultimate
  all_xbox_codes.txt            all xbox redeem codes found
  valid_xbox_codes.txt          xbox codes that are confirmed valid
  reward_point_hits.txt         accounts with microsoft reward points
  reward_point_hits_sorted.txt  same but sorted by point balance
  hypixel_stats.txt             hypixel stats for accounts that had them
  hypixel_ban.txt               hypixel banned accounts
  hypixel_blocked.txt           hypixel security blocked accounts
  hypixel_unban.txt             hypixel unbanned accounts
  hypixel_ranked.txt            accounts with a hypixel rank
  capes.txt                     accounts with minecraft capes
  set_name.txt                  accounts that had their name changed
  new_accs.txt                  accounts with no security info
  invalid.txt                   invalid or dead accounts
  locked.txt                    accounts that are locked
  2fa.txt                       accounts with 2FA enabled
  rate_limited.txt              accounts that hit rate limits after retries
  Inboxer/                      folder with per-keyword inbox hit files


DISCORD WEBHOOKS
----------------
edit webhook_config.json to set up notifications.

  default_webhook           main channel for MC and Xbox hits
  hypixel_unbanned_webhook  unbanned hypixel accounts only
  hypixel_banned_webhook    banned hypixel accounts only
  xbox_hits_webhook         xbox game pass accounts
  xbox_codes                xbox redeem codes


INBOX CHECKER
-------------
enable it in config.ini:

  inbox_checker = true
  inbox_keywords = Steam, Netflix, PayPal, Roblox, Riot

results show as Inbox: Steam(3), PayPal(1) in the output.


PROXIES
-------
- http proxies recommended. socks4 and socks5 also supported
- 50 threads with good proxies will do 200-300+ accounts per minute
- VPS in US or EU recommended for best speed
- ban checks require CONNECT to port 25565. use SOCKS5 if ban checks show unknown


RUNNING IN THE BACKGROUND
--------------------------
using screen (recommended):
  screen -S shulker
  ./ShulkerV2
  press ctrl+a then d to detach
  reconnect later with: screen -r shulker

using tmux:
  tmux new -s shulker
  ./ShulkerV2
  press ctrl+b then d to detach
  reconnect later with: tmux attach -t shulker

using nohup:
  nohup ./ShulkerV2 &

to check if it is running:
  ps aux | grep ShulkerV2

to stop it:
  pkill ShulkerV2


TRANSFERRING FILES TO YOUR SERVER
----------------------------------
using scp:
  scp ShulkerV2 user@yourserver:/path/to/folder/
  scp combos.txt user@yourserver:/path/to/folder/
  scp proxies.txt user@yourserver:/path/to/folder/
  scp config.ini user@yourserver:/path/to/folder/

using WinSCP on windows: connect to your server and drag the files over.


FILE PERMISSIONS
----------------
if you get a permission denied error:
  chmod +x ShulkerV2

if you get errors with config or result files:
  chmod 644 config.ini combos.txt proxies.txt webhook_config.json
  chmod 755 .


TROUBLESHOOTING
---------------
"permission denied" when running:
  chmod +x ShulkerV2

"cannot execute binary file":
  make sure you downloaded the linux version, not the windows .exe

results folder not being created:
  check write permissions:  chmod 755 .


AUTO RUN
--------
to skip startup questions and launch directly:
  1. open config.ini and go to the [auto_run] section
  2. set enabled = true
  3. fill in proxy_protocol, proxy_mode, display_mode, and threads
  4. save and launch


WHAT'S NOT IN THE FREE VERSION
-------------------------------
the following features are only available in premium:

  - Robux Sniper (auto-converts reward points to Robux)
  - Discord Nitro code fetching and validation
  - MS Balance checking
  - Donut SMP ban/stats checking
  - Donut SMP auto-pay
  - Telegram auto-check monitor
  - Auto Mark Lost (AML)
  - Web stats dashboard (stats.shulkerv2.xyz)
  - Better MS auth engine (more hits, fewer false invalids)
  - Proxyless session support (run without any proxies at all)
  - Frequent updates and bug fixes
  - Priority support

to upgrade: discord.gg/gU3BwPBvXb or chat.shulkerV2.xyz


PROBLEMS?
---------
the free version does not come with dedicated support. for help, visit
discord.gg/gU3BwPBvXb or upgrade to premium for priority support.


ANTIVIRUS FALSE POSITIVES
--------------------------
your antivirus may flag ShulkerV2 as malware. it is a false positive.

the binary contains no malware, spyware, keyloggers, or malicious code of any
kind. the reason AV engines flag it comes down to a few things:

  - Go static binaries are large and self-contained. AV heuristics treat large
    single-file executables with no external dependencies as suspicious.

  - it makes a lot of network requests. authenticating hundreds of Microsoft
    accounts in parallel looks identical to credential-stuffing malware from
    the outside. the AV cannot tell them apart by behaviour alone.

  - it handles email:password strings. any tool that reads this format triggers
    credential-theft heuristics regardless of what it actually does with them.

  - the binary is obfuscated. built with symbol obfuscation and packing to
    reduce detections — ironically this itself raises the heuristic score on
    some engines.

none of this means the tool is malicious. it means automated scanners cannot
distinguish a checker from actual malware based on patterns alone.

if you trust the tool, add an exclusion in your AV for the executable or its
folder. on Windows Defender: Settings > Virus & threat protection > Manage
settings > Add or remove exclusions.

if you do not fully trust it, run it on a VPS or a VM. a cheap VPS (Contabo,
Hetzner, DigitalOcean) keeps it completely isolated from your main machine and
gives better performance anyway.

do not run any checker on a machine you are not comfortable exposing.

