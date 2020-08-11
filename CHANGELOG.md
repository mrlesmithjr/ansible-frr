commit 8e8d43ce9bd224c728160a62b471372b6073d681
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 10:03:43 2020 -0400

    New files added based on Cookiecutter template

commit b519795c7d4aa9d098a6f0a62c5b4d70ac8624d7
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 10:03:30 2020 -0400

    Updated based on Cookiecutter template

commit cde2fad59a84cef64355e98161951d990a7b1e4d
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 10:00:00 2020 -0400

    Fixed linting issues

commit c635f6f89291f06e9bf9cdbc74755ab338ce3edb
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 09:54:50 2020 -0400

    Deleted old tests in favor of Molecule testing

commit c61565928b01442293aa8284e83b318ae9e5476c
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 09:54:29 2020 -0400

    Updated repo info based on Cookiecutter template

commit 19ad92b10e4958455d4fc01c0878c3f4a17aee30
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 09:50:05 2020 -0400

    Added new Molecule tests

commit 6b9644b671ab94c9663d680493a6e0cbdb361a45
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 11 09:49:25 2020 -0400

    Deleted previous Vagrant testing

commit b81135b13125260658f9ed27e75a0639d42f6e99
Author: Roman Danko <mail@romandanko.sk>
Date:   Thu Aug 6 08:55:40 2020 +0200

    Fixed ansible-lint errors

commit 626885b9faf3d7ec0ea418b1c4e7db050c5a57dd
Author: Roman Danko <mail@romandanko.sk>
Date:   Thu Aug 6 08:48:44 2020 +0200

    Fixed ansible-lint errors

commit 143cd1418a7c9a5f99b0cf06bf2d1e177ff8a772
Author: Roman Danko <mail@romandanko.sk>
Date:   Thu Aug 6 08:48:25 2020 +0200

    Removed testing by Python2

commit 035db193a140954e48ecd0ba7f1e79eeddf7ccf1
Author: James Farr Gomez <james@nertwork.com>
Date:   Fri Jul 24 11:20:58 2020 -0700

    Update main.yml

commit c9aa0ec3e1a7bf56c556ebb51ab58bcf57bed73f
Author: James Gomez <james@nertwork.com>
Date:   Fri Jul 24 17:14:18 2020 +0000

    Allows for Quagga configuration from this role.
    
    Features:
     - quagga configration (via routing_type var)
     - quagga configuration documentation
    Bug Fixes:
     - redistribute_v6 is fixed

commit bd8227eef0943aac87ec4c3e3604cec27ddc77bc
Author: Brian Andrus <oddomatik@users.noreply.github.com>
Date:   Thu Jul 2 13:45:08 2020 -0700

    Bionic should include debian.yml
    
    debian.yml includes the exact logic needed to deploy frr 7+ with bionic. There very well could be a better and more specific way to address this issue, but bionic does not like debian_legacy due to the specific version definition contained within.

commit cb1225fd904bed2341c0d9b21deecab53c8256f0
Author: James Gomez <james@nertwork.com>
Date:   Mon Apr 27 20:42:24 2020 +0000

    Adding Focal Support
    
    Right now the Focal distribution has the most recent FRR. The FRR repos
    do not support Focal currently, so to get this role to work we must use
    the default repo for now.

commit 4fbad4a1bfeb773e377abaec784fd6f5ee665039
Author: Roman Danko <mail@romandanko.sk>
Date:   Sun Mar 29 17:49:52 2020 +0200

    Added missing register variable in redhat.yml

commit 9740bef051dd6dd5e051878d175894b76bf3a80c
Author: Roman Danko <mail@romandanko.sk>
Date:   Sun Mar 29 16:40:02 2020 +0200

    Bugfix for tasks/config.yml:
     - removed conditional for meta flush_handlers task, which can't be used

commit 451ca6736296389705919de05e8d93c33e2f1aac
Author: Roman Danko <mail@romandanko.sk>
Date:   Sun Mar 29 16:37:11 2020 +0200

    Bugfix for frr.conf.j2 template:
     - iface_data['other'] should be already list, so it can't use function items()

commit d723d5b74b9859f6e1fb065a2ed548e391be6f9b
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 22:23:03 2020 +1100

    Corrected travis.

commit 505b75f1180282c4c086baeb739d160bfe889c1f
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 21:44:43 2020 +1100

    Pined molecule version.

commit 8e27cbe42e7228c829f6f873a2bebcb8b83cd35b
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 21:33:01 2020 +1100

    Revert "Updated formatting per molecule warnings."
    
    This reverts commit 2aa52d568428396ab1e599cd09d2f5e97ab4f53a.

commit 460e72dff798b21789fbcb6a22529b67eaea6a0c
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 21:32:39 2020 +1100

    Revert "Updated file name per dreprecated warnings."
    
    This reverts commit f9c9ff95445b8ede491747e38c73c7a98858b20d.

commit c041d4ffa3d2128a6ffdc27c2413b207c5da7bed
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 21:32:14 2020 +1100

    Revert "Changed linting to be molecule v3 compatilbe."
    
    This reverts commit 4965f68e5ae01ae5dc4a66bd71aff1ffec4ab4fa.

commit 2aa52d568428396ab1e599cd09d2f5e97ab4f53a
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 19:41:06 2020 +1100

    Updated formatting per molecule warnings.

commit f9c9ff95445b8ede491747e38c73c7a98858b20d
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 19:23:23 2020 +1100

    Updated file name per dreprecated warnings.

commit 4965f68e5ae01ae5dc4a66bd71aff1ffec4ab4fa
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Wed Mar 18 19:18:50 2020 +1100

    Changed linting to be molecule v3 compatilbe.

commit 534153b09d54dfb21a57c87f866dd2b0d922d2cf
Author: Ross <ross.thompson@thetradedesk.com>
Date:   Tue Mar 17 21:50:00 2020 +1100

    Adding files updated from iteritems to items.

commit 1df64bf21dfcb9446d8a59e76a3d117a8994e921
Author: James Gomez <james@nertwork.com>
Date:   Wed Dec 11 20:16:19 2019 +0000

    Installs python-frrtools as part of the frr install

commit 0744dd88b29741a1b42efbdcbf56d47f650cc989
Author: James Gomez <james@nertwork.com>
Date:   Wed Nov 6 22:28:59 2019 +0000

    Allow for APT REPO
    
    FRR has provided an apt repo for Debian based systems. This allows for
    an easier install/upgrade path and the existing provisioning has moved
    to debian_legacy where the new apt install has been created in
    tasks/debian

commit e689ff781deb794e212bd539581a51c1660a42f8
Author: James Gomez <james@nertwork.com>
Date:   Tue Nov 5 22:31:08 2019 +0000

    Python3 support
    
    This resolves the issue where iteritems() becomes items() in python3.
    This is to support python3 fully as python 2.7 is EOL starting Jan
    1, 2020.

commit d5e1f3734c520b53a3b5dcc4aabc87b3838a4fc2
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Tue Oct 8 20:35:32 2019 +0000

    prevent empty list items from iterating

commit fb2c6caf13a2a2b81d4f10e3e475c77431f424c2
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Mon Oct 7 21:54:57 2019 +0000

    we need to manage vtysh.conf

commit 80d75b49c650dd870da63fc1e04bea261c790981
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Tue Oct 1 02:37:54 2019 +0000

    ensuring is_peer_group is set before accessed

commit 616d724c72dfee28eced506793699415a81e1fc4
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Tue Sep 3 22:09:35 2019 +0000

    adding af option support for asn

commit 16fc32c50e18fa98e0eef3241d29a45c097efcef
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Tue Sep 3 20:55:17 2019 +0000

    adding support for address-family config lines

commit ade6abd9aa1b085f632a2e53cec6d38434d68b1e
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Thu Aug 29 22:40:41 2019 +0000

    fixing peer group sorting

commit 2176e2c16069db0d36e3feb3a5820c279a850034
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Thu Aug 29 19:40:34 2019 +0000

    updating readme

commit cfbedfb322012eed28d2ecd523e36abff5753ef0
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Thu Aug 29 19:28:43 2019 +0000

    adding forwarding and neighbor options

commit 1a4505482243a53463db527740da17c2455693fc
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Thu Aug 29 19:06:03 2019 +0000

    fixing ipv6 static route bug

commit 7766d82592b71f7c6ffcdc3e8e87856fb9931cb1
Author: James Gomez <james@nertwork.com>
Date:   Wed Aug 28 22:47:57 2019 +0000

    fix so neighbor is activated on address family

commit 143b52178aff9cb4c8d3ec7557237d4dac1b8266
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Wed Aug 28 22:41:42 2019 +0000

    more bugfix

commit 1d5166230541d3e97dae368ecfcccbf568e50135
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Wed Aug 28 22:32:42 2019 +0000

    fixing bugs yo

commit c43ac14e4ae4b13815c7eb87fb4fbb0226b86613
Author: James Gomez <james@nertwork.com>
Date:   Wed Aug 28 21:59:21 2019 +0000

    fixing syntax and cleanup for readability

commit aedcf8d33b63c8bd10f4295d43a6936c178fee36
Author: James Gomez <james@nertwork.com>
Date:   Wed Aug 28 21:59:21 2019 +0000

    fixing syntax and cleanup for readability

commit 52989767206d8fcc073e8ddb3f6ea5a3d570e336
Author: James Farr Gomez <james@nertwork.com>
Date:   Wed Aug 28 14:35:34 2019 -0700

    Update README.md

commit 232bb194b9c10553492d8e48a632cc05ce80031b
Author: James Gomez <james@nertwork.com>
Date:   Wed Aug 28 21:07:41 2019 +0000

    Family support for neighbors and networks
    
    This enables BGP family support for neighbors. This also enables the
    ability to configure v6 networks for BGP family v6.

commit ab243448a73f9a3fcc8d189a9b2f58110dcbb14a
Author: James Farr Gomez <james@nertwork.com>
Date:   Wed Aug 28 14:17:29 2019 -0700

    Update README.md

commit 80d74a75df8e43dc8684c2dc2f98f5fff57593e7
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Wed Aug 28 21:09:49 2019 +0000

    adding interface and ipv6 config options

commit 76d163e1766080f36944a3b38563046bcc1ebaa4
Author: Tomasz Baczyński <tomasz.baczynski@gmail.com>
Date:   Tue Aug 6 20:52:21 2019 +0200

    run "Fetch FRR version" task even in check mode

commit 9e2442a12cfd117f95133fa3736a3cd2cf3538d4
Author: Tomasz Baczyński <tomasz.baczynski@gmail.com>
Date:   Mon Aug 5 20:52:51 2019 +0200

    minor

commit 4743a95296bddc87e4b701b71fc5d3763947160f
Author: Tomasz Baczyński <tomasz.baczynski@gmail.com>
Date:   Sun Aug 4 22:56:57 2019 +0200

    add simple acl config
    
    add distribute-list for ospf router

commit 49df402bd3e640b6e23144c35960b48d978750a6
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Thu Aug 1 22:33:06 2019 -0400

    Resolved issues uncovered from initial Travis/Molecule testing
    
    - Closes #26

commit 67f50132ae408cd11a868675f2d83409280e6aba
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Thu Aug 1 22:25:45 2019 -0400

    First phase of Travis/Molecule testing
    
    This will be the first phase of testing which we will build upon. We
    will need to implement changes from #26 when identified to ensure that
    testing is successful.
    
    - Closes #24

commit 7c0abb40627c88f0221449672074f685bda1e1fd
Author: James Gomez <james@nertwork.com>
Date:   Mon Jul 15 22:24:23 2019 +0000

    This obtains the proper version format

commit a9d44725920534ac8fe62fbb1ffa39ecd10597e5
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Tue Jul 30 20:47:34 2019 +0000

    refactor and rename; no functional changes

commit f4186d169e82347daccd16e1212e8d34d1f7e891
Author: Ian Clark <ian.clark@dreamhost.com>
Date:   Fri Jul 26 23:54:53 2019 +0000

    adding a couple features

commit 1fb0be030cfa02b9c282579a113bc38bb82b32e4
Author: James Gomez <james@nertwork.com>
Date:   Mon Jul 15 22:24:23 2019 +0000

    This obtains the proper version format

commit 9b4395ae1b473ab259e787bdc993d79773ef7622
Author: James Gomez <james@nertwork.com>
Date:   Thu Jun 27 19:18:54 2019 +0000

    checking if proper version is installed before installing now

commit 1b7cbcf7500d0a46114a12eb3ded93be1b6f639b
Author: James Gomez <james@nertwork.com>
Date:   Mon Jun 24 19:40:41 2019 +0000

    ubuntu 18 needs iproute2

commit b865fe85f393aeafbfd16b1c7a580b24f6ae6d7e
Author: James <jfarr@jobs.nertwork.com>
Date:   Fri Jun 21 20:26:10 2019 +0000

    FRR install fix on Ubuntu 18
    
    Prior to this commit installs were being bypassed because the download
    directory was never changed. This was removed and instead of checking
    the download dir we check to make sure the frr package is instaled.

commit b0bdf0161cca2c747c9b9d33f591db9af3c6d24b
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Jun 6 11:09:39 2019 -0700

    Make sure FRR is started
    
    Currently, there are times with reload that the service will lock up. If
    this happens we will now make sure that the FRR instance is started at all
    times. Also instead of ignoring failures we will check if the files
    exist before moving them.

commit 0b455379f98848892a0e2995a28e9db5ab158b75
Author: David Wahlstrom <david.wahlstrom@dreamhost.com>
Date:   Thu May 16 12:48:16 2019 -0600

    The upstream package repo changed. Need to fix for ubuntu18
    
    This changeset makes it so ubuntu18.04 can actually download the frr
    package.
    
    Signed-off-by: David Wahlstrom <david.wahlstrom@dreamhost.com>

commit 432bacdfadd7ed5dadfa60d07690c519cae2eec4
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Apr 16 11:13:02 2019 -0700

    Fixing check mode
    
    This fixes failures and 'changes' reported during the check mode. This
    will allow for check mode to complete without throwing errors during a
    play.

commit aa5912439880537f6681a6844b93012ff932db07
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Mar 19 13:48:33 2019 -0700

    adding bgp neighbor timers README

commit 2e5e4ad5a779d7b817f1a10cfed221067e1cd5f9
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Mar 19 13:37:25 2019 -0700

    modifying defaults to show timers

commit eeb6625f15e7c9edd5333137dbfc515f0c1059e3
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Mar 19 13:36:13 2019 -0700

    adding in bgp instance timers

commit f23db3b61043e1c2121d0cd4494a9b978d62983f
Author: David Wahlstrom <david.wahlstrom@dreamhost.com>
Date:   Tue Mar 19 10:25:12 2019 -0600

    Adding support to define timers connect for bgp neighbor
    
    Adding support for ansible/jinja to search the frr variables for bgp
    `timers connect` option.
    
    Signed-off-by: David Wahlstrom <david.wahlstrom@dreamhost.com>

commit 734e15cf46b77feef7324e30e0e779122e5dbd23
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Wed Mar 6 08:19:11 2019 -0500

    Resolves #15

commit 80a1b52ba6413b0490ac848ee2ea7c89241b8b50
Author: James Gomez <james.farr@dreamhost.com>
Date:   Mon Feb 11 13:31:11 2019 -0800

    updating default variables

commit 875dbdc4de5c2ea503c24989769595172f192804
Author: James Gomez <james.farr@dreamhost.com>
Date:   Mon Feb 11 10:46:05 2019 -0800

    adding in frr_reload defaults

commit 68259b0fcf3bd0fd30d757011e25aea09ffde44f
Author: James Gomez <james.farr@dreamhost.com>
Date:   Mon Feb 11 10:41:01 2019 -0800

    Updating readme for upgrade/downgrade options

commit ba020297d689c50bdc09f50ad6cc132c900dfab5
Author: David Wahlstrom <david.wahlstrom@dreamhost.com>
Date:   Wed Feb 6 14:49:04 2019 -0700

    Keep connectivity after installing FRR on debian
    
    When installing the FRR package, something happens to cause the default
    routes to go away. In order to fix this, we simply need to run `netplan
    apply`. But this needs to be chained off of the package install. So the
    slightly goofy `shell` module for the package install and `netplan
    apply` is a tad hacky, but provides a specific pattern we're attempting
    to hit.
    
    Signed-off-by: David Wahlstrom <david.wahlstrom@dreamhost.com>

commit 188242ff3a277e4f388623a018627e041c757d82
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Jan 31 14:19:08 2019 -0800

    adding more bgp options and to readme

commit 6d2c0b4af811c2b61d1b847d8f98c276cad3c755
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Jan 24 17:33:21 2019 -0800

    OSPF changes
    
    These are changes to allow for a more robust implementation of OSPF.
    This allows us to have authentication and area types on the ospf areas
    and interfaces in OSPF.

commit e1978c2fefc81250b1d16368edf6a818c1c9a829
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Jan 22 12:14:33 2019 -0800

    Default Version changed to 6.0.2

commit 06181ca5ca5175e502904e5c83f286b181d80b76
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Jan 17 23:50:56 2019 -0800

    changing default to 6.0.2 and allowing upgrade

commit 210c0f74dad6dac147a8f560bff762aaabe194a0
Author: James Gomez <james.farr@dreamhost.com>
Date:   Wed Jan 16 22:16:15 2019 -0800

    fixing version for ubuntu 18 default

commit fb5f528c2ca12993d9234b7ce983a2f2ef069ebc
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Jan 15 14:50:26 2019 -0800

    fixes for frr conf to work

commit 1b461778e34f307f042390ac6e8dcd943efb3f56
Author: James Gomez <james.farr@dreamhost.com>
Date:   Fri Jan 11 11:37:23 2019 -0800

    fixing readabilty in the configuration file

commit 9aff1bb20d3015fbae00593b85574193c8bcaffc
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Jan 8 11:59:40 2019 -0800

    Adds Static Routes, Prefix Lists, Route Maps
    
    This is to allow for more routing options. Currently only OSPF and BGP
    were allowed and there were no Route Maps for either, this is to add
    thos features in to be used as needed.

commit 53a5f3ce49b748be91b24635389aef999c123c64
Author: James Gomez <james.farr@dreamhost.com>
Date:   Tue Jan 8 11:59:40 2019 -0800

    Adds Static Routes, Prefix Lists, Route Maps
    
    This is to allow for more routing options. Currently only OSPF and BGP
    were allowed and there were no Route Maps for either, this is to add
    thos features in to be used as needed.

commit 95927ce66536302c16e0179b4d0ec6b9b2ddc64d
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Dec 20 16:36:43 2018 -0800

    Reload support
    
    This modification is to install frr python tools to allow for reloading
    of frr instead of having to restart whenever a configuration change is
    made. I also changed a portion that would stop frr from reloading if the
    frr_router_id was not set.

commit 70fcea7308a724ab6ec4930185a54cc9a4350866
Author: James Gomez <james.farr@dreamhost.com>
Date:   Thu Dec 20 16:03:26 2018 -0800

    Ubuntu 18 support
    
    This is modifications to allow for newer FRR versions that support
    Ubuntu 18 and greater. Modifications were made on the upstream FRR
    release urls as well, which are reflected here as options past version
    4.0.

commit 5a0de8e5ced6f60fc0ab10ff119925092ae2048d
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Aug 28 20:25:39 2018 -0400

    Resolves issue #2

commit 4b5d299bb35bbe81930c870f797917b0e0d0b983
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sun Feb 4 11:43:08 2018 -0500

    Changed monitoring to use Docker containers on compute nodes.

commit 563af024417cbecc22568556aa0f883d8998605d
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sat Feb 3 15:19:57 2018 -0500

    Added ability to define BGP maximum paths.

commit 893552fb98cf1354a52c9cda5f9bd9d3747dd94d
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Fri Feb 2 15:49:51 2018 -0500

    Updated Grafana system template

commit fd47bcd9efcc3ee2ba2501465e8e60f90bb8deb2
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Fri Feb 2 00:56:02 2018 -0500

    Fixed missing CIDR for Vagrant node info. Also added screenshot of BGP Stats.

commit f9e1f03c82fecafcae6618870c696dd18a1a963a
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Fri Feb 2 00:49:07 2018 -0500

    Added monitoring capabilities and testing within Vagrant.

commit 9f8d829457f651253039dccdef51e5a7b0190a70
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Thu Feb 1 11:11:55 2018 -0500

    Added/updated roles
    
    Signed-off-by: Larry Smith Jr <mrlesmithjr@gmail.com>

commit acad4e8267c3afc2d9b04483583c0618d5cc8ca4
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Wed Jan 31 20:03:13 2018 -0500

    Merged config for bgp, ospf into single frr.conf

commit ef85b1c0ac75e7bd059be2dfc78e6a9ee8349eee
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Wed Jan 31 09:13:06 2018 -0500

    Added Docker to compute nodes in order to spin up some services

commit 11d1b2c38483946bb515cb633dabd416e23dab3e
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Jan 30 20:31:25 2018 -0500

    Added Vagrant environment info

commit 4eea219c4e41d35ea2dc585b23382b164c71ac3c
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Jan 30 20:22:58 2018 -0500

    Implemented Compute2 into BGP

commit 8eb850a7f8149337cc66d39ee11af118ac9df0a5
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Jan 30 20:03:08 2018 -0500

    Implemented leaf4 into BGP config

commit 606db8842a8140927b274c3597a88c3ef26cde9b
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Jan 30 19:44:02 2018 -0500

    Fixed BGP routing in current state

commit 9b852d49a7c5cf59e8e9d6a989ad69009e864c61
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Tue Jan 30 18:48:07 2018 -0500

    First commit of Vagrant setup using BGP.
    
    Currently not complete and only partially working as is.
    
    Signed-off-by: Larry Smith Jr <mrlesmithjr@gmail.com>

commit b685447b1919b69ea723185959ee4dd950ddf9cd
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 16:44:43 2018 -0500

    Fixed template if interfaces are not defined

commit c5c7635abb848394e285a1d3834139907f0502e1
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 14:20:59 2018 -0500

    Added additional default settings which should be present

commit 70ca94703b51a576af58c2008ac4dec1f6fc2bc1
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 13:32:05 2018 -0500

    Added check for frr_bgp being defined as []

commit 3fced373cc9c9f16f2db1feb746158e3741b48ff
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 12:47:40 2018 -0500

    Added CentOS 7 support

commit cca6ab193304867f0e346d5dc9e4dd6f2ddf373b
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 11:51:19 2018 -0500

    Added links for BGP, OSPF

commit 4426688284c628a6e3699e83636fd095ded4601b
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 11:50:59 2018 -0500

    Updated supported distros

commit 16272c2025d401740a158a60f84b033e49e86402
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Mon Jan 29 00:48:51 2018 -0500

    Added Debian support

commit 041af27f6ff1bc100f3607cd5be959b44d01e8b2
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sun Jan 28 22:13:02 2018 -0500

    Added initial BGP configuration functionality

commit d82cb4e70db79f90b06e284c84ec880ea2222151
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sun Jan 28 18:17:59 2018 -0500

    Create LICENSE

commit 6f9c227f298bedd4353fe76dbc4176a2cfdc1248
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sun Jan 28 18:17:06 2018 -0500

    Added TOC
    
    Signed-off-by: Larry Smith Jr <mrlesmithjr@gmail.com>

commit caa553c6a89c93ee1320e06a62ca791968f7e28a
Author: Larry Smith Jr <mrlesmithjr@gmail.com>
Date:   Sun Jan 28 18:16:47 2018 -0500

    first commit
