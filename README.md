# Правила использования парсера

- Парсер позволяет собирать данные возращая кортеж списков, список успешно собранных данных и список сайтов данные которых собрать не удалось. Доступные варианты использования:
    - BeautifulSoup: df_result, df_for_manual_work = SiteContentParserDSP().frame_content_searcher_bs(site_df)
    - Selenium: df_result, df_for_manual_work = SiteContentParserDSP().frame_content_searcher_selen(site_df)
    - BeautifulSoup & Selenium: df_result, df_for_manual_work = SiteContentParserDSP().start_parsing(site_df)
- Рекомендуется использовать вариант BeautifulSoup для повышения колличества собранных данных можно использовать комбенированный метод но это существенно увеличиит время сбора данных и потребуется немного усилий по установке вебдрайвера Chrome в используемую систему для корректной работы библиотеки Selenium. Без этого запуск кода будет не возможен.
- В инициализаторе класса присутствует список content_exceptions содержащий список фраз исключений по которым отбраковывается контент содержащий целиком данную фразу. При необходимости список можно дополнить новыми исключениями для более точной отбраковки сайтов. Данные в список заносить только в нижнем регистре без использования заглавных букв.
- Если по какойто причине количество ссылок слишком велико для сбора то рекомендуется сбор данных батчем например по 1000 сайтов. site_df[:1000]
- Так как цель создания парсера сбор данных для последующей классивифации интересующих сайтов то настоятельно рекомендуется не DDoS-ить сайты поторными запросами. При необходимости сбора данных для класссификации новых сайтов, требуется исключать из выборки для нового парсинга сайты класс и тип контента которых уже определены, это позволит уменьшить время сбора нужных данных, уменьшит нагрузку на собственную сеть и интернет канал, сэкономит ресурсы ПК на котором запускается код и в принципе это будет более этичным поведением в интернет пространстве.
