# Prosjektoblig---IS-114-Individuell-
Oppgave g) Norsk flagg

one= (overlay-xy(square(100, "solid", "red"), 110, 0, rectangle(30, 250, "solid", "navy")))

two= (overlay-xy(one, 150, 0, rectangle(180, 100, "solid", "red")))

three= (overlay-xy(two, 0, 110, rectangle(330, 30, "solid", "navy")))

four= (overlay-xy(three, 0, 150, square(100, "solid", "red")))

five= (overlay-xy(four, 150, 150, rectangle(180, 100, "solid", "red")))

five



include shared-gdrive("dcic-2021", "1wyQZj_L0qqV9Ekgr9au6RX2iqt2Ga8Ep")
include gdrive-sheets
include data-source
ssid = "1RYN0i4Zx_UETVuYacgaGfnFcv4l9zd9toQTTdkQkj7g"
kWh-wealthy-consumer-data =
  load-table: komponent, energi
    source: load-spreadsheet(ssid).sheet-by-name("kWh", true)
    sanitize energi using string-sanitizer
end
fun energi-to-number(str :: String) -> Number:
  doc: "If s is not a numeric string, default to 0."
  cases(Option) string-to-number(str):
    | some(a) => a
    | none => 0
  end
where:
energi-to-number("") is 0
energi-to-number("48") is 48
end
