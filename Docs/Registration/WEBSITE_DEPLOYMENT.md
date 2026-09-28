# KINGDOMS LIVE — опубликовано на GitHub Pages
Дата: 2026-09-28. Стоимость: $0. Платные услуги и домен не приобретались.

- Репозиторий: https://github.com/Magasah/kingdoms-live
- Сайт: https://magasah.github.io/kingdoms-live/
- Privacy: https://magasah.github.io/kingdoms-live/privacy.html
- Terms: https://magasah.github.io/kingdoms-live/terms.html
- Contact: https://magasah.github.io/kingdoms-live/contact.html
- Источник Pages: GitHub Actions, build_type=workflow, HTTPS enforced.
- Workflow: .github/workflows/pages.yml публикует только Website/.
- Официальные actions: checkout@v6, configure-pages@v5, upload-pages-artifact@v4, deploy-pages@v4.

## Стратегия репозитория
Основной Unity-проект не имел Git-репозитория; Assets занимают около 315 MB.
Создан отдельный сайт-репозиторий в Publish/kingdoms-live (~2.4 MB файлов).
Unity Assets, бинарные сборки, кеши, Config, логи и учётные данные не публикуются.
Канонический сайт остаётся в Website/. Рабочий Git checkout: Publish/kingdoms-live/.
Исходники игры не изменялись; повторная сборка Unity для этой задачи не нужна.

## Дальнейшее обновление
1. Измените Website/ в основном проекте.
2. Скопируйте изменённые файлы в Publish/kingdoms-live/Website/, сохраняя относительные пути.
3. В Publish/kingdoms-live выполните git add Website, git commit и git push.
4. Дождитесь успешного Publish KINGDOMS LIVE website в GitHub Actions.
5. Откройте публичные HTTPS-страницы. Используйте только публичный HTTPS URL в форме TikTok.
README и workflow выделенного репозитория обновляются непосредственно в его checkout.
Не копируйте весь Unity-проект в публичный репозиторий.

## Проверки
Главная, Privacy, Terms, Contact, CSS, favicon и изображения доступны по HTTPS (HTTP 200).
Ссылки работают под /kingdoms-live/. Отчёт: Reports/Registration/public-validation.txt.
Проверка секретов: Reports/Registration/security-check.txt.
Юридические страницы и контакт обновлены: kingdomslive.game@gmail.com, Tajikistan, September 28, 2026.
Единственное незаполненное поле — юридическое имя оператора. LIVE-доступ пока не предоставлен.
Файл проверки URL: см. TIKTOK_URL_VERIFICATION.md.
