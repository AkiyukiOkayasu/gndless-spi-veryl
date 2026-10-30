# gndless_spi

SPI masterとSPI mode型、MISOサンプルエッジ型を提供します。

依存はVeryl stdのみです。CPOL/CPHAのMode 0〜3、`DATA_WIDTH`、`CLK_DIV`、busy/done、CS setup/hold、MISOのサンプル点の契約は`SpiMaster`のdoc commentを参照してください。`CLK_DIV`は4以上の偶数を指定します。転送はstart受付からdoneまでの単一transactionで、busy中は入力を保持しません。

MISOはSCLKに同期して変化するソースシンクロナス入力として、指定したエッジで直接サンプルします。非同期入力や遅延が大きい場合は利用側で同期化してください。`MISO_SAMPLE_EDGE`でMISOのサンプルエッジをCPHAと独立に選べます。

```veryl
inst spi: gndless_spi::SpiMaster::<gndless_spi::Types::SpiMode::Mode1> #(
    DATA_WIDTH      : 32,
    CLK_DIV         : 4 ,
    MISO_SAMPLE_EDGE: gndless_spi::Types::SpiSampleEdge::Leading,
) (...);
```
