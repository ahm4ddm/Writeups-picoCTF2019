# 1. Insp3ct0r
Penyelesaian
- Coba kita lakukan inspeksi elemen pada web
- Ternyata ada flag tapi masih kurang dua lagi, kita cari di file .css nya ternyata ada flagnya
`picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?1638dbe7}`

# 2. Don’t-use-client-side
Penyelesaian
- Coba kita lakukan inspeksi elemen pada web
- Disitu ada kode aneh yaitu funcition verify() lalu kita urutkan saja
`picoCTF{no_clients_plz_ce22dc}`
# 3. Logon
Penyelesaian
- Coba kita login dengan username dan password bebas
- Kita edit cookienya pakai ektensi yang ada di web lalu kita ganti valuenya admin jadi True
`picoCTF{th3_c0nsp1r4cy_l1v3s_6f2c20e9}`
# 4. Where are the robots
Penyelesaian
- Coba kita inspeksi elemen, dan ternyata tidak ada kode yang mencurigakan
- Coba di parameter url kita tambahkan robots.txt
- Lalu kita copy file yang path Disallownya
`picoCTF{ca1cu1at1ng_Mach1n3s_0ecd0}`
# 5. Client-side-again
Penyelesaian
- Coba kita lakukan inspeksi elemen, dan ternyata ada kode yang mencurigakan dibagian script
- Kita percantik kodenya dengan beauty javaScript
- Lalu kita copy code aneh itu diconsole web lalu rename agar mudah dibaca
- Disitu ada flagnya kita langsung mengurutkan saja
- Kita analisis bahwa flag awalan { dan berakhir pada }
`picoCTF{not_this_again_ea9191}`
# 6. Open to admins
Penyelesaian
- Kita analisa dari web tersebut ternyata kita focus ke cookienya aja
- Buat cookie dengan nama admin dan time value 1400
`picoCTF{0p3n_t0_adm1n5_effb525e}`
# 7. Picobrowser
Penyelesaian
- Ternyata butuh useragent pico untuk dapat flag
- Download user agent switch
- Ganti dengan picobrowser
`picoCTF{p1c0_s3cr3t_ag3nt_bbe8a517}`
# 8. Irish-Name-Repo 1
Penyelesaian
- Kita analisa dari hints ternyata bug di sql
- Coba kita masuk ke admin login dengan menggunakan sql injection
- User admin pass ' or 1=1 -- '
`picoCTF{s0m3_SQL_96ab211c}`
# 9. Irish-Name-Repo 2
Penyelesaian
- Ini mirip sama yang pertama tapi dua duanya tidak bisa diinputkan string sql jadi menurut saya
ini bisa diakali dengan cara membypass di user saja, dan password diisi huruf
- Coba login dengan user admin'-- ' pass terserahbebasasalhurufdanangka
`picoCTF{m0R3_SQL_plz_752d1173}`
# 10. Irish-Name-Repo 3
Penyelesaian
- Menurut saya ini gabungan dari 1 dan 2, saya mencoba untuk mendebug value saya ganti jadi 1
- Saya memasukkan string ' or 1=1 -- '
- Hasilnya jadi string ‘be 1=1 –‘ lalu membuat kepala saya pusing
- Saya stuck dan saya iseng iseng masukkan string ‘be 1=1 –‘ ke password Alhamdulillah langsung
ada flagnya
`picoCTF{3v3n_m0r3_SQL_c2c37f5e}`
# 11. Empire 1
Penyelesaian
- Setelah saya coba beberapa kali gagal, lalu saya menebak ternyata flagnya ada di bug sql
- Registrasi terlebih dahulu, lalu masuk add todo
- Masukkan ' || 'i' || ' untuk inject dengan concat
- Masukkan ' || (EXISTS (SELECT secret FROM user WHERE secret LIKE 'picoCTF{%')) || '
unutk konfirmasi flag yang ada di kolom secret
- Masukkan string sql ' || (SELECT secret FROM user WHERE username = 'user') || ' untuk
dapat flag
`picoCTF{wh00t_it_a_sql_injecta4dfbd62}`
# 12. Empire 2
Penyelesaian
- Ini hamper sama dengan empire 1, Cuma saya utek utek ini hamper 20 menit tidak ketemu
- Lalu saya dapat di google katanya bug nya ada di web framework
- Setelah saya selidiki ternyata web frameworknya flask ada bug
- Kita masukkan {{7*'7'}}
- Lalu kita masukkan {{config}}
- Taraaa ketemu tapi itu bukan flagnya sih wkwk
- Tapi itu ada clue bahwa flagnya ada di cookie
- Kita copy aja cookienya lalu decode
`picoCTF{its_a_me_your_flagf3d56a8a}`
# 13. Empire 3
Penyelesaian
- kita masuk ke webnya
- ini seperti empire 2
- tapi menurut saya bug ada di web framework
- setelah saya cari referensi banyak sih solusi agak panjang dan susah mengerti juga 0_0
- lalu saya dapat dapat referensi juga ternyata bisa dilihat melalu SSTI (Server Side Templete
Interface)
- lalu saya dapatkan code ssti injectionnya yaitu {{
''.__class__.__mro__[1].__subclasses__()[157].__init__.__globals__.__builtins__.eval("__import
__('os').popen('grep -R .').read()") }}
- kita copy di add todo
- berhubung banyak file yang dioutputkan jangan lupa pakai fitur search wkwkwk:v
`picoCTF{cookies_are_a_sometimes_food_404e643b}`