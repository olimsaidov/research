# Jarima Platformasi Texnik Lugʻati

Ushbu keng qamrovli lugʻat evolyutsiya tahlili hujjatlari davomida ishlatiladigan texnik atamalar, biznes tushunchalari va platformaga xos terminologiya uchun taʼriflarni taqdim etadi. U tadqiqotchilar, hukumat amaldorlari, dasturchilar va biznes strateglari kabi turli auditoriyalar oʻrtasida aniq tushunishni taʼminlash uchun maʼlumotnoma sifatida xizmat qiladi.

## Asosiy biznes atamalari

### AYHT (Avtomatlashtirilgan Yoʻl Harakati Xavfsizligi Tizimi)
Hukumatning yoʻl harakati qoidabuzarliklarini boshqarish boʻyicha rasmiy tizimi. Jarima rasmiy qayta ishlash uchun tasdiqlangan qoidabuzarliklarni yuborish uchun AYHT bilan integratsiyalanadi.

### Qoidabuzarlik/Huquqbuzarlik
Fuqarolar tomonidan videoga olingan va platforma orqali qayta ishlangan yoʻl harakati qonunbuzarligi. Har bir qoidabuzarlik aniqlash, koʻrib chiqish va yuborish bosqichlaridan oʻtadi.

### Hisobot
Yoʻl harakati qoidabuzarligi haqida video dalillarni oʻz ichiga olgan fuqaroning taqdimoti. Hisobotlar bir nechta huquqbuzarliklarga ega boʻlishi va turli holat oʻzgarishlaridan oʻtishi mumkin.

### Mukofot
Muvaffaqiyatli xabar berilgan qoidabuzarliklar uchun fuqarolarga beriladigan pul kompensatsiyasi. Telefon krediti, bank kartasi yoki xayriya xayriyalari orqali tarqatilishi mumkin.

## Texnik arxitektura atamalari

### OAuth2
Uchinchi tomon kirishini amalga oshirilgan sanoat standart avtorizatsiya tizimi. Ruxsat berilgan kodlar va mijoz maʼlumotlari oqimlarini qoʻllab-quvvatlaydi.

### MinIO
Video va tasvir saqlash uchun ishlatiladigan ochiq manbali obʼyekt saqlash tizimi. Jarima ortiqchalik va geografik taqsimot uchun bir nechta MinIO misollaridan foydalanadi.

### Redis/Carmine
Sessiya boshqaruvi, keshlash va vaqtinchalik maʼlumotlar uchun ishlatiladigan xotiradagi maʼlumotlar ombori. Carmine Redis uchun Clojure mijoz kutubxonasi.

### HoneySQL
SQL semantikasini saqlab qolgan holda tarkibiy, dasturiy soʻrov qurishni taʼminlaydigan Clojure uchun SQL yaratish kutubxonasi.

### Luminus
Jarima ilovasi tuzilishi uchun asosni taʼminlaydigan toʻliq stek Clojure veb-ramka, jumladan marshrutlash, oʻrta dastur va maʼlumotlar bazasi migratsiyalari.

## Qayta ishlash liniyasi atamalari

### Kodlovchi xizmat
Video transkodlash va standartlashtirish uchun javobgar tashqi mikroxizmat. Izchil format va sifatni taʼminlash uchun videolarni qayta ishlaydi.

### Aniqlovchi xizmat
Videolarni tahlil qilish, qoidabuzarliklarni aniqlash, davlat raqamlarini chiqarish va qoidabuzarlik turlarini aniqlash uchun AI-quvvatli mikroxizmat.

### Navbat
core.async kanallari yordamida asinxron qayta ishlash mexanizmi. Asosiy navbatlarga kodlash navbati, aniqlash navbati va toʻlov navbati kiradi.

### Majburiy aniqlash
Oddiy navbat tartibini chetlab oʻtib, videoni aniqlash navbatida darhol qayta ishlash uchun ustuvorlik beradigan qoʻlda bekor qilish bayrogʻi.

## Platforma komponentlari

### Fuqaro
Qoidabuzarliklar haqida xabar beradigan oxirgi foydalanuvchilar. Turli cheklovlar va imkoniyatlarga ega oddiy fuqarolar yoki korporativ hisoblar boʻlishi mumkin.

### Inspektor/Xodimlar
Xabar qilingan qoidabuzarliklarni koʻrib chiqadigan va AYHTga yuborish boʻyicha qarorlar qabul qiladigan hukumat xodimlari.

### Tashkilot
Odatda flot boshqaruvi uchun oʻzlari ostida bir nechta fuqaro hisoblariga ega boʻlishi mumkin boʻlgan biznes subyektlari.

### Mijoz (OAuth)
API orqali platformaga kirish uchun vakolatli uchinchi tomon ilovalari. Mijozlar qayta ishlash talablariga taʼsir qiladigan ishonch darajalariga ega.

## Maʼlumotlarni boshqarish atamalari

### Qayta koʻrib chiqish
Muvofiqlik va nosozliklarni tuzatish maqsadlarida muhim obʼyektlarga kiritilgan oʻzgarishlarni kuzatuvchi audit izi tizimi.

### Migratsiya
Luminus migratsiyalari yordamida maʼlumotlar bazasi sxemasi versiyasini boshqarish. Har bir migratsiya yuqoriga/pastga SQL skriptlariga ega.

### Webhook
Qoidabuzarlik holatlari oʻzgarganda OAuth mijozlariga yuborilgan HTTP qayta qoʻngʻiroqlar, real vaqtda integratsiyalarni taʼminlaydi.

## Toʻlov atamalari

### Kash
Telefon kreditini toʻldirish va baʼzi karta toʻlovlari uchun ishlatiladigan asosiy toʻlov shlyuzi xizmati.

### UzCard
Oʻzbekistondagi milliy toʻlov kartasi tizimi. Integratsiya balansni tekshirish va ommaviy toʻlov imkoniyatlarini oʻz ichiga oladi.

### Konsolidatsiyalangan toʻlovlar
2024-yilda amalga oshirilgan ommaviy toʻlovlarni qayta ishlash tizimi samaradorlik uchun bir nechta mukofotlarni bitta tranzaksiyaga guruhlaydi.

## Xavfsizlik atamalari

### Buddy
Sessiya boshqaruvi va kriptografik funksiyalarni taʼminlaydigan Clojure autentifikatsiya va avtorizatsiya kutubxonasi.

### Ikki omilli autentifikatsiya (2FA)
SMS tasdiqlash kodlari yordamida sezgir hisoblar uchun qoʻshimcha xavfsizlik darajasi.

### Doira
Mijoz qanday resurslarga va operatsiyalarga kirishi mumkinligini belgilaydigan OAuth2 ruxsat toʻplamlari (masalan, hisobot-yuborish, karta-telefon-oʻqish).

## Ishlash atamalari

### Gorizontal masshtablash
Ortgan yukni koʻtarish uchun koʻproq server namunalarini qoʻshish qobiliyati. Holatga bogʻliq boʻlmagan dizayn va taqsimlangan komponentlar orqali erishiladi.

### Zanjir uzgich
Tashqi xizmatlar (AYHT kabi) mavjud boʻlmaganda kaskadli xatolarni oldini oladigan xatolarga chidamlilik namunasi.

### Tikker
Chime kutubxonasi yordamida rejalashtirilgan fon ishi. Misollar muntazam oraliqlarda ishlaydigan kodlovchi-tikker va aniqlovchi-tikkerni oʻz ichiga oladi.

## Integratsiya atamalari

### AYHT tokeni
Autentifikatsiya yukini kamaytirish uchun 24 soat davomida keshlangan hukumat yoʻl harakati tizimiga kirish uchun autentifikatsiya maʼlumotlari.

### Ommaviy/Xususiy soʻnggi nuqtalar
Xavfsizlik va ishlashni optimallashtirish uchun ichki (xususiy) va tashqi (ommaviy) kirish uchun alohida URL-manzillar bilan MinIO konfiguratsiyasi.

### Hosila aktivlar
Kodlangan videolar, eskizlar va aniqlash qoplamali videolar kabi asl yuklashlarning qayta ishlangan versiyalari.

## Umumiy qisqartmalar

- **API**: Ilova dasturlash interfeysi
- **CRUD**: Yaratish, Oʻqish, Yangilash, Oʻchirish operatsiyalari
- **GPS**: Global joylashuvni aniqlash tizimi (qoidabuzarlik joyi uchun ishlatiladi)
- **UI/UX**: Foydalanuvchi interfeysi/Foydalanuvchi tajribasi
- **ROI**: Investitsiyadan qaytish
- **SLA**: Xizmat darajasi kelishuvi
- **CI/CD**: Uzluksiz integratsiya/Uzluksiz joylashtirish
- **SMS**: Qisqa xabarlar xizmati (bildirishnomalar uchun ishlatiladi)
- **MFA**: Koʻp omilli autentifikatsiya
- **SDK**: Dasturiy taʼminot ishlab chiqish toʻplami