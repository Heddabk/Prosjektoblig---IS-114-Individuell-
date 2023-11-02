# Prosjektoblig---IS-114-Individuell-
Prosjektoblig 1
Oppgave g) Norsk flagg

one= (overlay-xy(square(100, "solid", "red"), 110, 0, rectangle(30, 250, "solid", "navy")))

two= (overlay-xy(one, 150, 0, rectangle(180, 100, "solid", "red")))

three= (overlay-xy(two, 0, 110, rectangle(330, 30, "solid", "navy")))

four= (overlay-xy(three, 0, 150, square(100, "solid", "red")))

five= (overlay-xy(four, 150, 150, rectangle(180, 100, "solid", "red")))

five

Prosjektoblig 2
Oppgave 2
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
energi-to-number("30") is 30
energi-to-number("37") is 37
energi-to-number("5") is 5
energi-to-number("4") is 4
energi-to-number("15") is 15
energi-to-number("12") is 12  
end
  
kWh-wealthy-consumer-data

ny-tabell = transform-column(kWh-wealthy-consumer-data, "energi", energi-to-number)
ny-tabell

fun bil(): 
  energy-per-day = ((50/10) * (10))
  energy-per-day
end

bil()

fun sum-energi():
  t = transform-column(kWh-wealthy-consumer-data, "energi", energi-to-number)
  sum(t, "energi")
end
sum-energi() + bil()

bar-chart(ny-tabell, "komponent", "energi")
