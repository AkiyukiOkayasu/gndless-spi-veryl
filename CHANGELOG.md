# Changelog

## [0.1.4] - 2026-10-27

### Fixed

- Mode 1/3の先頭SCLKをCS setup後まで遅らせ、`LeadHold`状態で先頭High幅を半周期確保するようにした
- Mode 1/3のCS setupがCLK_DIVに比例しない問題を修正した
- Mode 1/3のMISOサンプルをtrailing edge後のLow期間へ移し、leading edgeでサンプルしていた問題を修正した

### Added

- Mode 1/3の外部スレーブモデルtestとCS setup testを追加した

### Changed

- `CLK_DIV`/`DATA_WIDTH`の下限と奇数`CLK_DIV`の扱いをdoc commentへ明記した

## [0.1.2] - 2026-10-14

- `SpiMaster`のMode 1/3受信サンプルをSCLK立ち下がりから1クロック後（`LowWait`）へ移動
  - SCLK立ち下がりでSDOを更新するスレーブ（ADS8688等）のデータ遷移に対する受信マージンを確保
- Mode 1/3の先頭SCLK High幅を定常時と同じ半周期へそろえる
  - 補正がないと先頭Highだけ1クロック分となり、ADS8688等のスレーブの最小High幅仕様を割る

## [0.1.1] - 2026-08-08

- 公開moduleのparam/port doc commentと日本語説明を整理
- doc commentの句点と体言止めの表記を整理
- 各testのdoc commentへmode別の検証対象を明記
- `SpiMaster`の`div_cnt`/`bit_cnt`をparameter導出の必要最小幅へ変更

## [0.1.0] - 2026-07-31

### Changed

- 公開型packageをproject名と重複する`Spi`から`Types`へ改名
- `spi_pkg`を`Spi`へ改名し、SPI masterを独立packageへ移動
- `SpiMaster`へtransactionとMode 0〜3のedge契約を示すWavedromを追加
