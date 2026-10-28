# CookBook — Üçüncü hissə

CookBook reseptləri axtarmaq, kateqoriyalar üzrə gəzmək və yeməklərin hazırlanma qaydalarına baxmaq üçün hazırlanmış Next.js tətbiqidir. Bu hissədə resept məlumatları TheMealDB API-dən server tərəfdə yüklənir.

## İstifadə olunan texnologiyalar

- **Next.js 16 App Router** — səhifələr, dinamik marşrutlar və server komponentləri.
- **React 19** — istifadəçi interfeysi və interaktiv porsiya/checklist hissəsi.
- **JavaScript** — tətbiqin məntiqi.
- **CSS** — rəngli, mobil uyğun dizayn və resept kartları.
- **TheMealDB API** — resept, kateqoriya, şəkil və hazırlanma məlumatları.
- **GitHub və Vercel** — kodun saxlanması və tətbiqin yayımlanması.

## İmkanlar

- Ana səhifədə API-dən gələn kateqoriyalar və kateqoriya şəkilləri.
- Resept adına görə axtarış.
- Reseptin adı, şəkli, kateqoriyası, ölkəsi, ərzaqları və hazırlanma addımları.
- Kateqoriyaya klikləyərək həmin kateqoriyadakı reseptlərə baxmaq.
- Porsiya sayını dəyişmək və hazırlanma addımlarını checklist-də işarələmək.
- Məlumat yüklənərkən loading görünüşü.
- API xətası zamanı yenidən cəhd düyməsi.
- Mövcud olmayan resept üçün 404 səhifəsi.
- API boş nəticə qaytaranda “Resept tapılmadı” mesajı.

## Quraşdırma və işə salma

Kompüterdə Node.js və npm quraşdırılmış olmalıdır.

1. Layihə qovluğunu VS Code-da açın. Bu qovluqda package.json faylı görünməlidir.
2. VS Code terminalında asılılıqları quraşdırın:

   npm install

3. Tətbiqi başladın:

   npm run dev

4. Terminalda görünən localhost ünvanını brauzerdə açın. Adətən bu, http://localhost:3000 olur.

Tətbiqi dayandırmaq üçün terminalda Ctrl + C basın.

## Səhifələr

- / — ana səhifə və API-dən yüklənən kateqoriyalar.
- /reseptler — resept siyahısı.
- /reseptler?q=chicken — yemək adına görə axtarış nümunəsi.
- /reseptler/52772 — ID-si 52772 olan resept nümunəsi.
- /reseptler/kateqoriya/Seafood — Seafood kateqoriyasındakı reseptlər nümunəsi.

## Layihə quruluşu

    app/
      error.js
      layout.js
      not-found.js
      page.js
      globals.css
      reseptler/
        error.js
        layout.js
        loading.js
        page.js
        [id]/
          page.js
        kateqoriya/
          [ad]/
            page.js
    components/
      Navbar.js
      ReseptKart.js
      ReseptDetallari.js
    lib/
      themealdb.js

## API sorğuları

Tətbiq TheMealDB-nin V1 API-sindən və öyrənmə/test açarı olan 1-dən istifadə edir. Reseptləri yükləmək üçün internet bağlantısı lazımdır.

- Adla axtarış: search.php?s=...
- İlk siyahı: search.php?f=c
- ID ilə resept: lookup.php?i=...
- Kateqoriyalar: categories.php
- Kateqoriyaya görə reseptlər: filter.php?c=...

API sənədləri: [TheMealDB API Guide](https://www.themealdb.com/documentation)

Əsas səhifələr resept məlumatlarını app/data.js sabit massivindən deyil, API-dən alır. data.js faylı layihədə başqa səhifələr üçün saxlanıla bilər.

## GitHub və Vercel

Dəyişiklikləri GitHub-a göndərmək üçün layihə qovluğunun terminalında:

    git add .
    git commit -m "CookBook README-ni yenilə"
    git push

GitHub repozitoriyası Vercel-ə qoşulubsa, yeni push-dan sonra deployment avtomatik başlaya bilər. Vercel-də layihənin Root Directory-si package.json olan qovluq olmalıdır.
