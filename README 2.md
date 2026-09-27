# Penalti Bilik Yarışı — Sosial siyasətin obyekti və subyekti

Penalti-üslublu bilik oyunu. Suallar **Mövzu 2. Sosial siyasətin obyekti və subyekti** sənədinə əsaslanır: düzgün cavab — qol, səhv cavab — atılan zərbə tutulur.

Tək fayldan (`index.html`) ibarətdir. Quraşdırma, framework və server tələb etmir.

## Oyun ideyası

- İştirakçı əvvəlcə **futbolçusunu seçir** (6 stilizə edilmiş, tam uydurma personaj — real klub və ya idmançı deyil).
- Hər iştirakçıya **5 sual** düşür, çətinlik **1-ci səviyyədən 5-ci səviyyəyə** qədər get-gedə artır.
- Hər suala **15 saniyə** vaxt verilir.
- Cavab seçiləndən sonra futbolçu qaçıb zərbə vurur:
  - **Düzgün cavab → QOL** (top qapıya girir, tor "titrəyir", konfetti).
  - **Səhv cavab və ya vaxtın bitməsi → top tutulur** (qapıçı doğru küncə tullanır).
- Nəticə ekranında neçə qol vurulduğu və hər sualın düzgün cavabı (mənbə bölməsi ilə birlikdə) göstərilir.

## Sual bazası

- Ümumilikdə **40 sual**: 5 səviyyə × 8 sual.
- Hər oyunda (hər iştirakçıda) hər səviyyədən 1 sual təsadüfi seçilir — bu, 5 sualdan ibarət, get-gedə çətinləşən dəst yaradır. Cavab variantlarının yeri də hər dəfə qarışdırılır.
- Görülən suallar brauzerin `localStorage` yaddaşında saxlanılır və **iştirakçıdan iştirakçıya təkrar olunmur** — hər səviyyədəki 8 sual bitənə qədər (yəni 8 iştirakçıdan sonra) həmin səviyyə üçün dövr yenidən başlayır.
- Ana səhifədəki «Sual bazasını sıfırla» düyməsi bu yaddaşı təmizləyir.

## Sualları dəyişmək

`index.html` faylında `SUAL BAZASI` şərhindən sonrakı `BANK` massivini redaktə edin:

```js
Q("Sual mətni?", "Düzgün cavab", ["Səhv 1", "Səhv 2", "Səhv 3"], "Mənbə bölməsinin adı")
```

Massivdə 5 qrup var (1-ci qrup ən asan, 5-ci qrup ən çətin sual səviyyəsi). Hər qrupda ən azı 8 sual saxlamaq məsləhətdir ki, təkrarsızlıq məntiqi düzgün işləsin.

Futbolçuları dəyişmək üçün eyni fayldakı `ROSTER` massivini redaktə edin (ad, forma nömrəsi, rəng).

## GitHub Pages ilə yayımlamaq

1. Yeni repozitoriya yaradın və `index.html` ilə bu README-ni (kök qovluğa) yükləyin.
2. **Settings → Pages → Build and deployment** bölməsində **Deploy from a branch** seçin.
3. Branch olaraq `main`, qovluq olaraq `/ (root)` seçib **Save** düyməsini basın.
4. Bir neçə dəqiqədən sonra oyun `https://<istifadəçi-adı>.github.io/<repozitoriya-adı>/` ünvanında birbaşa açılacaq.

Lokal işə salmaq üçün faylı brauzerdə açmaq kifayətdir.

## Texniki qeydlər

- Futbolçu, qapıçı və top qrafikləri SVG ilə, "render edilmiş" (gradient bevel, kölgə) görünüş verən stilizə formalarla çəkilib — hərəkət yüngül CSS keçidləri ilə canlandırılır. Bu, əsl 3ds Max render deyil, amma oxşar "3D toy" görünüşü verir.
- Şrift Google Fonts-dan (Montserrat) yüklənir; internet olmayanda sistem şrifti işləyir.
- Səs effektləri WebAudio ilə yaradılır (fayl tələb olunmur) və oyun ekranındakı düymə ilə söndürülə bilər.
- Mobil və masaüstü qurğularda işləyir.
