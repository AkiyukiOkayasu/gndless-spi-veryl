# Changelog

## [Unreleased]

- `SpiMaster`のMode 1/3受信サンプルをSCLK立ち下がりから1クロック後（`LowWait`）へ移動
  - SCLK立ち下がりでSDOを更新するスレーブ（ADS8688等）のデータ遷移に対する受信マージンを確保

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
