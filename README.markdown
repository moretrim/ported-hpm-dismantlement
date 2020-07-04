Ported HPM Dismantlement
========================

Description
-----------

This is a Victoria 2 submod meant to be overlaid on top of [HFM]. It is unlikely to work well or at
all with other mods based on HFM as the functionality provided by this submod requires modifying
some fairly important files.

Due to the latter reason this submod also incorporates the option to disable colonial railroading.
See the features down below.

[HFM]: https://github.com/SighPie/HFM

Installation
------------

Since this is a submod, you need the [Historical Flavour Mod][HFM] installed already. Follow
instructions there to install it if you haven’t already.

Grab the [0.1.1 release].

[0.1.1 release]: https://github.com/moretrim/ported-hpm-dismantlement/releases/tag/v0.1.1

Install this as you would any other mod. When installed properly, the `ported_hpm_dismantlement.mod`
file and the `ported-hpm-dismantlement` directory should live side-by-side with the respective
`.mod` file and directory of the underlying mod.

In the Victoria 2 launcher you should see an entry for the submod:

![launcher](./launcher.jpg)

The `50: ` prefix should ensure that the submod appears *before* the underlying mod. If it doesn't
the submod is unlikely to work at all. (For advanced use, this prefix can be modified to tweak load
order.) Make sure you are loading *both* the submod & the underlying mod (in the picture that's
stock HFM), as indicated by the check marks.

Once a game has been started you can verify that the submod has been loaded correctly by looking at
the decision screen. It should include the following decision somewhere near the top of the list of
decisions:

![decision](./decision.png)

You can click the decision at any time to harmlessly dismiss it.

Features
--------

### Optional Colonial Raidroading

This submod incorporates an option to disable colonial railroading ([HFM PR #157]). This option is
not enabled by default should the player wish to play by the same rules as in base HFM 1.27I.

[HFM PR #157]: https://github.com/SighPie/HFM/pull/157

### Ported HPM Features

Ported features are based on [HPM 0.4.5.2]. They are:

[HPM 0.4.5.2]: https://github.com/arkhometha/Historical-Project-Mod/tree/v0.4.5.2

- Add the organisation decisions, e.g. the decisions to show/hide government decisions. Without
  HPM's array of decisions though this doesn't do much.

- Updated colonial organisation decisions. Relative to HFM, these are now usually taken later in the
  game.

- Updated colonial RGO decisions when organising a colony, allowing the country to tailor colony
  output to their needs.

- Updated dismantlement. Relative to HFM this means:

  * proper dismantlement of Indian lands & satellites
  * proper dismantlement of Indonesian lands
  * cleaner dismantlements of colonies, e.g. returning Namibian lands to whichever country is in
    charge of the colony of Namibia (regardless of status during the dismantlement war)
  * infamy costs when entire countries (colonial or otherwise) change hands are based on population
  * better player control of dismantlements, as vassal countries & countries which have lost *any*
    war in the past 5 years are ineligible for dismantlement spoils (in particular: settling for a
    white peace counts as losing a war)

These features also come with bugfixes, among which some are pending HFM bugfixes:

- [HFM/#174]

[HFM/#174]: https://github.com/SighPie/HFM/pull/174

Some have been accepted into later HPM versions:
- [HPM/#39]
- [HPM/#43]

[HPM/#39]: https://github.com/arkhometha/Historical-Project-Mod/pull/39
[HPM/#43]: https://github.com/arkhometha/Historical-Project-Mod/pull/43

Note that this port does *not* include e.g. the updated colonial CB system of HPM.

Known Issues
------------

Some things have not been brought up to speed and may result in new & possibly unexpected behaviour:

- During dismantlement some countries may not end where they would in either HFM or HPM. They can
  end up independent, or be improperly annexed by a country including the dismantled power.

  This includes Egypt, which is known to become independent in some circumstances.

- Colonial countries (e.g. Nigeria, Indonesia) may not civilise on time, or at all.

- Unorganised colonial territories can end up in the hands of a secondary power vassal country that
  participated in the dismantlement ([HPM/#133]).

  [HPM/#133]: https://github.com/arkhometha/Historical-Project-Mod/issues/133

Release History
---------------

### 0.1

The 0.1 series of releases are all save compatible from one version to the next:

#### 0.1.2-dev (in development)

- Add missing dismantlement machinery. The missing parts may have been causing dismantlements to
  take longer than intended, though this should have mostly affected the dismantlement of player
  countries.

#### [0.1.1](https://github.com/moretrim/ported-hpm-dismantlement/tree/v0.1.1)

- cherry-pick [HFM/#174]

#### [0.1.0](https://github.com/moretrim/ported-hpm-dismantlement/tree/v0.1.0)

The original release.

Remarks To Mod Makers
---------------------

If you are interested in incorporating HPM features by using some or all of the changes included in
this submod, I would urge caution. This submod works by porting some HPM features piecemeal—because
it is intended as a stopgap.

This author is of the opinion that HFM would benefit better from HPM 0.4.\* features through proper
merging. This submod in fact started as a project to study how hard such a merge would be, to which
my tentative conclusion is: though time-consuming it should be doable, certainly at least for large
swathes of the mod. However because this submod is limited in scope it ended up not being written
like that.

In the eventuality that such a merge ever happens the changes present in this submod are likely to
be obsolete and conflicting. For this reason all I suggest to anyone that incorporates them is to
ensure that all changes are easily revertible.

In addition most if not all design decisions taken in the writing of this submod are documented
through comments (e.g. 'HPM 0.4.5.2 port: bugfix').
