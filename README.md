This repository exists to test a proposed change to the [Dotty](https://github.com/lampepfl/dotty) CI,
to automatically open an issue if the nightly build fails.

The testing triggered CI runs using various events, forcing failures of the different jobs, and observed
whether an issue was created in each circumstance. The results are summarized in the tables below.


### Event: `workflow_dispatch` (proxy for `schedule`)

|Status             | Test                         | Workflow Run     | Issue      | Expectation
|:-----------------:|------------------------------|------------------|------------|-----------------
|:heavy_check_mark: | All jobs succeed             | [Run 11][run11]  | - none -   | No issue created
|:heavy_check_mark: | Fail `test_non_bootstrapped` | [Run 13][run13]  | [#9][i9]   | Issue created
|:heavy_check_mark: | Fail `test`                  | [Run 15][run15]  | [#10][i10] | Issue created
|:heavy_check_mark: | Fail `test_windows_full`     | [Run 17][run17]  | [#14][i14] | Issue created
|:heavy_check_mark: | Fail `community_build_a`     | [Run 19][run19]  | [#11][i11] | Issue created
|:heavy_check_mark: | Fail `community_build_b`     | [Run 21][run21]  | [#12][i12] | Issue created
|:heavy_check_mark: | Fail `test_sbt`              | [Run 23][run23]  | [#13][i13] | Issue created
|:heavy_check_mark: | Fail `test_java8`            | [Run 25][run25]  | [#15][i15] | Issue created
|:heavy_check_mark: | Fail `publish_nightly`       | [Run 27][run27]  | [#17][i17] | Issue created
|:heavy_check_mark: | Fail `nightly_documentation` | [Run 29][run29]  | [#18][i18] | Issue created
|:heavy_check_mark: | Multiple failures            | [Run 31][run31]  | [#16][i16] | Issue created

---

For all event types other than `schedule`, the expectation is that no issue is created.

---

### Event: `pull_request`

|Status             | Test                         | Workflow Run
|:-----------------:|------------------------------|--------------------------------------------------
|:heavy_check_mark: | All jobs succeed             | [Run 2](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518661084)
|:heavy_check_mark: | Fail `test`                  | [Run 3](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518661399)
|:heavy_check_mark: | Fail `test_windows_fast`     | [Run 4](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518661681)
|:heavy_check_mark: | Fail `community_build_a`     | [Run 5](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518662025)
|:heavy_check_mark: | Fail `community_build_b`     | [Run 6](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518662345)
|:heavy_check_mark: | Fail `test_sbt`              | [Run 7](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518662651)
|:heavy_check_mark: | Multiple failures            | [Run 8](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518662948)
|:heavy_check_mark: | Fail `test_windows_full`     | [Run 9](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518663177)

### Event: `push`

|Status             | Test                         | Workflow Run
|:-----------------:|------------------------------|--------------------------------------------------
|:heavy_check_mark: | All jobs succeed             | [Run 10](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518668176)
|:heavy_check_mark: | Fail `test_non_bootstrapped` | [Run 12](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518669229)
|:heavy_check_mark: | Fail `test`                  | [Run 14](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518670285)
|:heavy_check_mark: | Fail `test_windows_full`     | [Run 16](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518671484)
|:heavy_check_mark: | Fail `community_build_a`     | [Run 18](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518672583)
|:heavy_check_mark: | Fail `community_build_b`     | [Run 20](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518673602)
|:heavy_check_mark: | Fail `test_sbt`              | [Run 22](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518674656)
|:heavy_check_mark: | Multiple failures            | [Run 30](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518678764)

### Event: `push` sbt-dotty tag

|Status             | Test                         | Workflow Run
|:-----------------:|------------------------------|--------------------------------------------------
|:heavy_check_mark: | All jobs succeed             | [Run 32](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518684181)
|:heavy_check_mark: | Fail `community_build_a`     | [Run 33](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518684624)
|:heavy_check_mark: | Fail `community_build_b`     | [Run 34](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518685095)
|:heavy_check_mark: | Fail `test_sbt`              | [Run 35](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518685742)
|:heavy_check_mark: | Fail `publish_sbt_release`   | [Run 36](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518686259)
|:heavy_check_mark: | Multiple failures            | [Run 37](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518686704)

### Event: `push` release tag

|Status             | Test                         | Workflow Run
|:-----------------:|------------------------------|--------------------------------------------------
|:heavy_check_mark: | All jobs succeed             | [Run 38](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518692371)
|:heavy_check_mark: | Fail `test_non_bootstrapped` | [Run 39](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518692889)
|:heavy_check_mark: | Fail `test`                  | [Run 40](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518693463)
|:heavy_check_mark: | Fail `test_windows_full`     | [Run 41](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518693955)
|:heavy_check_mark: | Fail `community_build_a`     | [Run 42](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518694496)
|:heavy_check_mark: | Fail `community_build_b`     | [Run 43](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518695116)
|:heavy_check_mark: | Fail `test_sbt`              | [Run 44](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518695617)
|:heavy_check_mark: | Fail `test_java8`            | [Run 45](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518696154)
|:heavy_check_mark: | Fail `publish_release`       | [Run 46](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518696518)
|:heavy_check_mark: | Fail `release_documentation` | [Run 47](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518696942)
|:heavy_check_mark: | Multiple failures            | [Run 48](https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518697232)

[run11]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518668872
[run13]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518669845
[run15]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518671049
[run17]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518672161
[run19]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518673235
[run21]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518674293
[run23]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518675351
[run25]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518676479
[run27]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518677386
[run29]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518678311
[run31]: https://github.com/griggt/trial-open-issue-on-ci-failure/actions/runs/518679287

[i9]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/9
[i10]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/10
[i11]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/11
[i12]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/12
[i13]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/13
[i14]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/14
[i15]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/15
[i16]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/16
[i17]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/17
[i18]: https://github.com/griggt/trial-open-issue-on-ci-failure/issues/18
