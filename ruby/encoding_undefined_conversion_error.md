# ShiftJISのデータのエラー(Encoding::UndefinedConversionError)

```bash
Traceback (most recent call last):
        3: from libs/onduty_doctor/schedule.rb:73:in `<main>'
        2: from libs/onduty_doctor/schedule.rb:14:in `do_generate'
        1: from libs/onduty_doctor/schedule.rb:33:in `csv_data'
libs/onduty_doctor/schedule.rb:33:in `encode': "\\xFB\\xFC" from Shift_JIS to UTF-8 (Encoding::UndefinedConversionError)
```

データの中に 「はしご高(`髙`)」が入っていた。
エンコーディングを `Windows 31J`にして読み込むように修正。

```
URI.parse(CSV_URL).open.read.encode(Encoding::UTF_8, Encoding::Shift_JIS)
URI.parse(CSV_URL).open.read.encode(Encoding::UTF_8, Encoding::WINDOWS_31J)
```


https://teratail.com/questions/230233