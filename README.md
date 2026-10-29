# whisper-cadangan

Cadangan model **Whisper small (CTranslate2 int8)** untuk skill `lihat-video` (faster-whisper).
Sumber utama tetap paket npm `@skillninja/shortmovie-telop-model-p0..p3@1.0.0`; repo ini dipakai bila paket itu hilang.

- Bobot model: OpenAI Whisper small, lisensi MIT (lihat `LICENSE`). Konversi CTranslate2 int8 dari paket @skillninja (MIT).
- `model.bin` dipecah menjadi `model.bin.part00`–`part05` (45 MB per bagian).
- sha256 `model.bin` utuh: `ca732cb1379efc49417d028465f543d83a39de2c61f3027678de103dc404ce73` (sama dengan `model.sha256` paket npm).

## Pulihkan

```bash
M=<folder>/model; mkdir -p $M && cd $M
B=https://raw.githubusercontent.com/Maninwhite152/whisper-cadangan/main
for f in model.bin.part00 model.bin.part01 model.bin.part02 model.bin.part03 model.bin.part04 model.bin.part05 \
         config.json preprocessor_config.json tokenizer.json vocabulary.json SHA256SUMS model.sha256; do
  curl -fsSL -o "$f" "$B/$f"
done
sha256sum -c SHA256SUMS
cat model.bin.part0* > model.bin && sha256sum -c model.sha256 && rm model.bin.part0*
```

Checksum tidak cocok = jangan pakai model itu.
