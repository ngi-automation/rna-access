# Automated RNA Access Installation Guide #
**For Agilent NGS Workstation Option B**

## Contents ##
1. [Description](#Description)
2. [Requirements](#requirements)
3. [Installation](#installation)
4. [Protocol](#protocol)
5. [License](#license)

## Description ##
This document describes how to set up the automated RNA Access protocol for the Agilent NGS Workstation created at NGI Stockholm.

## Requirements ##

Item                                 | Note
:------------------------------------|:---------
Agilent NGS Workstation              | :warning: Option B configuration only
Eppendorf twin.tec 96 PCR plate      | Eppendorf, cat# 0030 128.672 (int); 951020460 (US)
Nunc deepwell 1.3 mL plate           | Thermo Scientific, cat# 260251
ABgene 2.2 mL storage plate Mk.II    | Thermo Scientific, cat# AB-0933

Labware definitions                  | Provided in `all_labware_liquids.vzp`
Liquid classes definition            | Provided in `all_labware_liquids.vzp`

\* provided in `all_labware_liquids.vzp`

#### Included files ####

```
illumina_spri.pro
rna-access.js
rna-access.rst
rna-access.VWForm
rna-access_atailing-ligation_setup.pro
rna-access_capture.rst
rna-access_cdna-spri_setup.pro
rna-access_elution.pro
rna-access_filler.pro
rna-access_hyb.pro
rna-access_ligation-spri_setup.pro
rna-access_ligation.pro
rna-access_pcr.pro
rna-access_reaction.pro
rna-access_spri-atailing_setup.pro
rna-access_spri-pcr_setup.pro
rna-access_spri_setup.pro
rna-access_wash.pro
all_labware_liquids.vzp
resources/1313497192_media_controls_light_pause.png
resources/1313497517_media_controls_light_play.png
resources/clear_inventory.bat
resources/clear_inventory.sql
```

## Installation ##
### Download files ###

##### Using Git #####
Clone into `https://github.com/ngi-automation/rna-access.git` from the `Protocol Files` directory:

```bash
cd "C:\VWorks Workspace\Protocol Files"
git clone https://github.com/ngi-automation/rna-access.git
```

Alternatively, download the compressed folder from:
[`https://github.com/ngi-automation/rna-access/archive/master.zip`][zip]
and extract to `C:\VWorks Workspace\Protocol Files`. Rename the resulting `rna-access-master` folder to `rna-access`. The path to the folder containing the extracted files should then be `C:\VWorks Workspace\Protocol Files\rna-access`.

### Configure ###
#### Labware and and liquid class definitions ####
Use the import feature in VWorks from `File › Import`in the toolbar and select the `all_labware_liquids.vzp` file included. See the [VWorks Knowledge Base][import] for more information.

#### Device files ####
Device files and profiles are system specific and will not be provided. Two different Bravo configurations are used in the RNA Access protocols (one being the "standard" configuration):

##### Standard configuration #####
Position | Type | Part#
-------: | ---- | -----
1&ndash;3, 8  | Deck Platepad | `G5498b#004`
4, 6     | Peltier Thermal Station (Inheco) | `G5498b#021`
5        | Orbital Shaking Station | `G5498b#033`
7        | Magnetic Bead Accessory | `G5498b#008`
9        | Thermal Station (ThermoCube) | `G5498b#036`/`7`/`8`

##### Capture configuration #####
Same as above but with the following modification:

Position | Type | Part#
-------: | ---- | -----
6        | Thermal Station w Deepwell Plate Insert | `G5498b#012`

For reference see Agilent's [accessories catalog][catalog] for the Bravo.

Each `.pro` file must have the correct device file set:

Protocol file | Device file
-------- | -----------
`rna-access_reaction.pro` | Standard
`rna-access_pcr.pro` | Standard
`illumina_spri.pro` | Standard
`rna-access_hyb.pro` | Standard
`rna-access_filler.pro` | Standard
`rna-access_wash.pro` | Capture
`rna-access_elution.pro` | Capture
`rna-access_atailing-ligation_setup.pro` | Standard
`rna-access_cdna-spri_setup.pro` | Standard
`rna-access_ligation-spri_setup.pro` | Standard
`rna-access_spri-pcr_setup.pro` | Standard
`rna-access_spri-atailing_setup.pro` | Standard
`rna-access_spri_setup.pro` | Standard

See the [VWorks Knowledge Base][device-file] for more information on how to select the device file.

## Protocol ##

See the NGI Stockholm/SciLifeLab [Standard Operating Procedure][sop] (work in progress).

## License ##
> Licensed under the Apache License, Version 2.0 (the "License");
> you may not use this file except in compliance with the License.
> You may obtain a copy of the License at
>
> http://www.apache.org/licenses/LICENSE-2.0
>
> Unless required by applicable law or agreed to in writing, software
> distributed under the License is distributed on an "AS IS" BASIS,
> WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
> See the License for the specific language governing permissions and limitations under the License.

The full license can also be found in the file LICENSE and must included when redistributing the software.

If this method is used to generate results for publication we ask that you include a reference to this repository, something like:
```
Automation protocols made available by the National Genomics Infrastructure Stockholm at https://github.com/ngi-automation/rna-access
```
*VWorks Automation Control*, *Bravo* and other things relating to the *Agilent NGS Workstation* are trademarks owned by Agilent Technologies, Inc. (Santa Clara, CA 95052-8058, US).

*RNA Access* is a trademark owned by Illumina, Inc. (San Diego, CA 92122 US)

[email]: mailto:joel.gruselius@scilifelab.se "E-mail author"
[ngi]: https://www.scilifelab.se/facilities/ngi-stockholm/ "NGI Stockholm"
[scilife]: https://www.scilifelab.se "SciLifeLab"
[zip]: https://github.com/ngi-automation/rna-access/archive/master.zip
[import]: http://www.velocity11.com/techdocs/AutomationSolutionsKB/vworks4_ug/11_Troubleshooting.15.03.html#2005458
[catalog]: http://www.chem.agilent.com/Library/catalogs/Public/5991-0369EN.pdf
[sop]: https://goo.gl/wlRVMg
[device-file]: http://www.velocity11.com/techdocs/AutomationSolutionsKB/vworks4_ug/02_CreateProtocolBasic.04.08.html#1981042

---

>[National Genomics Infrastructure][ngi] at [SciLifeLab][scilife]  
<joel.gruselius@scilifelab.se>  
April 2016
