\# Практикум: explain и индексы



Стенд: MongoDB в Docker (`docker compose up -d`, `reset`). База `logs`, коллекция `events`, 1200 документов.

Планы снимала скриптом `plan.py`, разбирала на Paste the Plan.



\## Сводная таблица



| № | Индекс | Возвращено | Документов просмотрено | Ключей просмотрено | Шаги плана | Ссылка |

|---|--------|-----------|------------------------|--------------------|------------|--------|

| 1 | нет | 33 | 1200 | 0 | COLLSCAN → SORT | https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:zVXbbuM2EP2XwT6qgeRLnOgtcZw22LhOo7SLxaIoxuRIYUORWnLkyGv43wvSt2QvyWILFH2yzJkzlzNzyBVQ12hU5g9yXlkDOWSQwMeW3PJGozHkIF-BwZp8g4IgB20rf0QLMuwhAWUkdZdKM7mCGPIStacEGnSe5G8hTMC_QSMh_7ACTQvS8YQ-Qg7knHWwXicr8OQWKiTY2Rpc1jFJNMvWIStr_qp9dKkY8mGartd_rrfl_oL-HnIYn2eD4eTkAhJoNJoxint6S8vnFtuwqtWnGPFO1TRVWisPeZpAjd1V6InkzBVWt8HF31III_ftHZzOjHzJqxBo_J2ddI22kj53eFTGKFMFokNTnrEKDBez2ztIwFvHN8hMLlrZQ_5Ttk6gpvpa1Yohz9LByXB0nKYJ8LIJUK_qRlOcS9NysQl4iDyeXV8X47NfIYEyzuw_GI5UjgRvdqu07hGdDChw9DcJJhm695B_CL7UkYhcFowcYx1OWiHIe8jZtZSAuSVunQlk9vtPgJ9Nky2jfktLP-mwVtF9d3phxZPTrBdYfJq_Iv-Vobyed-JZ1cgUMz1a9-BD9P4wAZQLNGIHNUQyoGLubPP_vSK9KdHjggIJwRy48mzdkwPlJ7PL-PWvtmRDBDIW6hMV1nEo7jQ7yRJoPckL5R_2y-obpfWG1fhJMgLZOqwo4KPp_7N3PzqpMItvTio7Hv3wpL4mhATkF2sYxIFaR11MdlVvBSJsXUfaVlCq8Av7m_hA7J61A13JjuQtu8m3udus1LNdeiPn24sfgpncgtyVKW1wureeIYde2s-Gkvon87QMV28M0Rul2SiBxf5tGR2lR4PwwFSKDy-OoNN0SMNhOZKyh9lpKeaD_qgcpafHJz0xGPRwPs964viQ_AYd1sTkYu3KhO1HHZ-bSxTE521ZkgtLeb7koOMnGvjSe4rdrOWm5QsrXsZcW_vQNnG9r8JRTVIh04UVbeB5it3L-J1jYVsn6Gdn22aK3ZRq65avVDrF7lxb8aBMFYS6wfzusXqtxRtn79Vc8Q49JVfRzEytqWyx1ezzPGdS3tmC-Hv7KIjfKSPt42UQhf_eji7DDIPsxtaws3ojC0Fjjd4rMTGVMhRmbh8gz9b_AA |

| 2 | service, level, ts, duration\_ms | 33 | 33 | 43 | IXSCAN → FETCH | https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:7VZLc9s4DP4rGUwPe1Azkh9xolv82mayqt0q3cekGQ8sQg4bilRIypGb8X_fIeVndjfpcXdmTxLBDyAAfgD4DFSXArn8lbThSkIMEQTwWJFeTQVKSRriZ5BYkCkxI4hBqIU5pSVJayAALhnVYy4s6ZQsxDkKQwGUqA2xT86M03-HkkF8-wyCliS8hB4hBtJaaVivg2cwpJfcHbDdK3FV-EP8Nqs0Wq7krDAesrAQd8Nwvb5bb9z9gOYeYhj0o053dD6EAEqBcoDZPV3TCmIYjvtRFI36EIAqLS_4d2_xhheUcCG4gTgMoMD6ysVEbKJTJSoHMZ_JmWG78PagS8leQ6UZSnOjRnUpFKOXgCcuJZcLl2gXlLG4cBkej24GH3xuy8qmjXC_e_V7Orj8CAE80GqK1pJulLf5i4JtlqMArIH4fRQcpy9ab-7tIxbO4kZ1Fs284iyaWTN7H80OlGaOFdwklbDcZ3Mb4kYwRXtvjty4vdv54X6dI-575Mituzxuvkj-WNHOJjepp8-BYIrachR7ifN-R9lWAIxrymxD4FzpJ9RsS86-qiR74Rvcft3x6ysEJ4erOzjw3AE9SRvU5tdDfERwm2B9TavgJOHymlZ-5zhG-KkbhsEJl_lpeAd36_U6AE3fKLPE3M1v80A1ZZ5HqUXr_d1LqiwjYyC2uqIA5GeylZaOSO32geILJltlUVzTyoxqLLiHd9ob8VBlB-IjK55w5u_4-Pa5I2N5gbZh4ZPSD6Y5E9kSZbZVlETM6UB80Sz-4CSY99ngklz85FeajFX6QMDNaDL2xtlfAkChCZlrA5P5twb9ev38m8L5v5b_k7XsL-5FfRkix5ModMqluSFjqWGDWw61Kku_dn0AhfAtYLTl3iaPmSoKPzKfIefuC7uBm_tZe5SC_ajcBbuZrME_z80AjNLWyRperQN4x-ab-Q5um_SS9JXMlQPdK2MhhlbYjrqM2ufzMHcT1pto9cKoF8By94TonYanHceyBbf7h0VGF2GXut28x1gLo4s8m3favbwXXpydt7JOp4XzedTKzvaHT1FjQZa0951LVx8o_KtijBnZfpXnpFP-nforSz7pnfNu7yz0xf8SnWA9qWxZ2aHKXtf5RamHqvSd48qJCmIcLQ1VVrk8J1i_rr8FpqrSGf2sVVUmWCdUKL16w9ME675Q2QOXi1Rp2-h8Mbh4K8SpVvd8zu1WOyG9oIlMlFyodNMOj8-5ZOxGpWR_NI6U7G9cMvU0dv3N_GhEY3eHrnkOlLRaiaaqMxoINIZnI7ngktydqwfXzv4E
 |

| 3а | duration\_ms, service, level, ts | 33 | 33 | 378 | IXSCAN → SORT → FETCH | https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:7VZLb9s4EP4rwaCHPbCB5Eec6BbH9jZIXWcjdx9IA2MsjhzWFKmSVGI38H9fkPIrTZMU3csusCeJw_mG8_wwD0CLUqJQv5OxQitIIAYGXyoyy0uJSpGB5AEUFmRLzAgSkHpmD-mOlLPAQChOi4GQjkxKDpIcpSUGJRpL_DdvxuPfoOKQXD-ApDuSQUJfIAEyRhtYrdgDWDJ3wj-wuStxWYRHwjWvDDqh1aSwQWXmIGlH0Wp1s1q7-w7tLSRw1o1b7f5xDxiUEtUZZrd0QUtIoDfoxnHc7wIDXTpRiK_B4lgUNBRSCgtJxKDAxbmPifjIpFpWXsVekTfDt-HtlE4Vf0krzVDZse4vSqk5fatwL5QSauYT7YOyDmc-w4P--OxdyG1ZubQW7m7T0dUYGFht3CU6RyZgnYXkbbxiUFDxXhTCQRJHreN25yiKGLhl6aGccqyke9b0-Z_p2ekHYDCn5Z7tR7mP2a5UMdsUNGY7D0JLfMAivLiDTuLJGjiJJwE2iSfOTt76hhN2WEknQqE22VsLLtHd2iduXN_s-eEPa0f8rwv33hP7UYkvFW1tCpuGztwTXKJxAuVO4r3fTkODAReGMlfPRq7NPRq-6fuurhT_jm_wSzuK2IFQ-WF0A488hetP287-BOxg_xRUN3F4xTAetdb6N6iE-OB6iIsLWrKDoVAXtLyBm9VqtWJg6DNljrjvqk0iaEFZ6NHUoQsO7yRVlpG1kDhTEQN1Ra4yyjdps7kH3J8SX2ztUF7Q0vYXWIhavXO8lvd0ti9vPn5_RvZ7zf76w33rRIGOwpjeazO3kLTiJgPkd6iyDVIRcQ_yHp3Ux78ESR5gFu_I56A2Ysg6bfYEwvZHgxAgfxIDSkPIPc2Mpp9r7Zfm818Wzz-ji7qs6DAVXynVxgXn4qNjBpUl3hN2vh0gWwopay4Nv8QD0GmDM_L4F3K3JaCfy15I0LPZa7V_Onv_8-F_kg9D4b6lKEsUeqV1xIBXpR2TDe0c1cee0WUZzoFNUcpApP1NB65TmemiCEvNA-TCf2G7EuVhGwptvQlzt8xsA1rvPuz5zaYe2kfT-oZP1xsYrOoskjlXufZKt9o6SKARNeM2p-bxNMr9DhRMNDpR3GFwt13yOofRYcs32ky43eqX0UnUpnY773DewPgkz6atZifvRCdHx42s1WrgdBo3sqPd45dosCBHJvgulB8RlGHvG2BGrlvlORk_9d2l88S_xzJPtYe4GFWurFxPZy9j3ms9r8rAH-deVBAX6Kins8rneYiLl_EbxVRXJqNfja7KIS6GVGizfMXTIS66UmdzoWaeCWvMR4uz10K8NPpWTIXboIdkZjRSQ61mOl2T4uN3Tjkf65Tcj8aRkvtDKK7vB57i7I9GNPA19BR6ppUzWtaDndGZRGtF1lczocjXXM8hiVd_Aw|

| 3б | service, level, duration\_ms, ts | 33 | 33 | 33 | IXSCAN → SORT → FETCH | https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:7VZLb9s4EP4rwaCHPbCB5Eec6BbH9jZIXWcjdx9IA2MsjhzWFKmSVGI38H9fkPIrTZMU3csusCeJw_nmxZkP8wC0KCUK9TsZK7SCBGJg8KUis7yUqBQZSB5AYUG2xIwgAaln9pDuSDkLDITitBgI6cik5CDJUVpiUKKxxH_zZjz-DSoOyfUDSLojGST0BRIgY7SB1Yo9gCVzJ7yDzV2JyyI4Cde8MuiEVpPCBpWZg6QdRavVzWod7ju0t5DAWTdutfvHPWBQSlRnmN3SBS0hgd6gG8dxvwsMdOlEIb4Gi2NR0FBIKSwkEYMCF-c-J-Ijk2pZeRV7Rd4M36a3UzpV_CWtNENlx7q_KKXm9K3CvVBKqJkvtE_KOpz5Cg_647N3obZl5dJauLtNR1djYGC1cZfoHJmAdRaSt_GKQUHFe1EIB0kctY7bnaMoYuCWpYdyyrGS7lnT53-mZ6cfgMGclnu2H9U-ZrunitnmQWO2iyC0xAcsgscddBJP1sBJPAmwSTxxdvLWN5yww0o6ER5qU7214BLdrX0SxvXNXhz-sA7E_7pw7yOxH5X4UtHWprBp6Mw9wSUaJ1DuJD767TQ0GHBhKHP1bOTa3KPhm77v6krx78QGv7SjiB0IlR9GN_AoUrj-tO3sT8AO9k9BdZOHVwzjUWutf4NKyA-uh7i4oCU7GAp1QcsbuFmtVisGhj5T5oj7rtoUghaUhR5NHboQ8E5SZRlZC4kzFTFQV-Qqo3yTNpt7wP0paTJw2qG8oKXtL7AQtXrneC3v6Wxf3nzsf0b2e83-uuO-daJAR2FM77WZW0hacZMB8jtU2QapiLgH-YhO6uNfgiQPMIt35GtQGzFknTZ7AmH7o0HoZv4kB5SGkHuaGU0_19ovzee_LJ9_Rhf1s6LDVHylVBsXgouPjhlUlnhP2Pl2gGwppKy5NPwSD0CnDc7I41-o3ZaAfq56oUDPVq_V_unq_c-H_0k-DA_3LUVZotArrSMGvCrtmGxo56g-9owuy3AObIpSBiLtbzpwXcpMF0VYah4gF_4L25UoD9tQaOtNmrtlZpvQevdhz2829dA-mtY3fLrewGBVV5HMucq1V7rV1kECjagZtzk1j6dR7negYKLRieIOg7vtktc5jA5bvtFmwu1Wv4xOoja123mH8wbGJ3k2bTU7eSc6OTpuZK1WA6fTuJEd7ZxfosGCHJkQu1B-RFCGvW-AGbluledk_NR3l84T_x7LPNUe4mJUubJyPZ29jHmv9bwqA3-ce1FBXKCjns4qX-chLl7GbxRTXZmMfjW6Koe4GFKhzfKVSIe46EqdzYWaeSasMR8tzl5L8dLoWzEVboMekpnRSA21mul0TYqP_ZxyPtYpuR_NIyX3h1Bc3w88xdkfzWjg39BT6JlWzmhZD3ZGZxKtFVlfzYQi_-Z6Dkm8-hs
 |

| 4 без индекса | нет | 10 | 1200 | 0 | COLLSCAN → SORT | https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:7VbJcts4EP2VVFeOjEuUJcvmzdomKoexEiqzlONytYAmhRgEaACUpaT071OA1sgzdmY5zGFOJJqv0ct7aPAb0KKSKNTPZKzQChKIIYKHmsxyLFEpMpB8A4Ul2QoZQQJSF_aE5qSchQiE4rQYCunIZOQgyVFaiqBCY4l_8Nt4f0lzkv7lNT1AAmSMNrBabQK9RTuDBNqD5tlpqz2ACCqJqodsRle0hAS6p4N-9_ysDxHoyolSfEUntJqIklIhpbCQNCIocTHy2RC_NpmWtYfYj-S34bvE9qBLxZ9DZQyVnejBopKa0zHgUSglVOFb5MuyDgvfm3ejdDSBCKQohbssda0cJHHDt6mqXbZG7eHDwaT3Fv7s6-jXrHf5HiK4p-UYnSOjDnoZR8BrE_pwV1pI3sSrDRvvsQw8edxdfHeAunvjyRU2raUTobXbejeGMbqZPQhyc3sU5ebWR7GflHioaecubBYIPzCM0TiBcm_xme1E1oyAC0PMrSWXa_OIhm_l1NW14t-lATef16L5DNGr3estPEkPblJcXNEyepUKdUXLW7hdrbzQDH0h5oh7xrZ10IJY4D9z6EK8vaVmjKyFxJmaIlAfydVGeQF4NnewIwU67VBe0dIOFliKHTyY-5odmQ_DF2T_SEcvxx1YJ0p0FOI_anNvIYnjCJDPUbGtoyLi3ieg_OI3QZKHlcU5-frX3wxZp82BQdjB9TCo7S9q-m-m3vjXU29EwJ_0HqUh5H7yXE-_rNHPn8H_Ujn_z4N_NA9CA4_0YIkCX96_shOyjtak-GXf6KoK6zBKUMowRQZbDWzawHRZouI-z1z4J-xuyTxckAcVbK_ACKw2zn94Sl44cJv0hCokddGx2XYkvebTzWUcdiEzJzNSufZ7zbR1kECzcRq3OZ2eTxu5v1RDpGanEXcimO_u-85J46TldVAIt_8LYHTRaFO7nXc4b2J8kbNp67STdxoXZ-dN1mo1cTqNm-xsH3yMBktyZAJTQnl9ogy_AENk5Lp1npPJxFfqLh2Fw9E6b3fOGuHwHaNTXFzXrqpdX7Pnfd5pfV9X4eSOvKkkLtBRX7O6JOU3et5_C8x0bRj9ZHRdpbhIqdRm-UKmKS66UrN7oYpMG7f2-WSxeKnEsdEzMRVu652SKehapVoVOtuMo-_jXHI-0Rm5H60jI_eLUFw_Dv18sT9a0dBz6IdXTytntFwfRkY9idYKNlCFUOQ51_eQxKvfAQ
 |

| 4 с индексом | level, duration\_ms (-1) | 10 | 10 | 10 | IXSCAN → FETCH → LIMIT |https://dfrancour.dev/tools/mongodb-paste-the-plan#v1:tVRtb-M2DP4vxH30CttJmtTf2jTZimuWru42DMMwMBLtaJUlnySnyR363wcqzUuvRXsbtk9xKJIP-fAhvwCtW43K_ELOK2uggAwS-NSR29xoNIYcFF_AYEO-RUFQgLa1P6EVmeAhAWUkradKB3IlBSgq1J4SaNF5kj9xGo7XtCLNHx_oExRAzlkHj49PQD-gX0IBg0l-2usPJpBAq9GMUSzpI22ev9g2qEZ9xqCsuVMNzZTWykORJtDg-oqrITl3pdUdu_hb4jRyX9jB6dzIt7xKgcbf2cm61VbS1w4PyhhlaqaI2_IBa-amnN_eQQLeunCDIZCLr7Jzsd4_Gw_Fd9ljAg0116pRAYos7Y8Gw9M0TUCz5byxnYn2BMKm5aReNa2myHXbhXILdcAcz6-vy_H5j5BAFefwJuFSORJhO-nKugd0Mtod_UUikOSOPBS___GYAK1JRH7KgMFztoOlE4K8hyK4jhIwtxQ6Z5ggLnzv9tWEgg2oP9LGT9bYqOi-s15acWTN8jR9jl-Tf4Xo93EnPqgGA0WkB-vuPWfP8gRQrtCIXaghkhwVsbPt_98U6W2JHlfEJPAzc-WDdUcG5Sfzafz6nya_pQgDluozldYFLjsf5b0EOk_yUvn7vTR9q7Te8h0_ScbAYB3WxPHx6b_Q0jH7o39CPxN8RP_oOf9pnv5r_l-TdwLyhbi4fNQ6qn2yK_tJ9sI2DRrJHVeKf2F_7V6QsmNjO_nXR653807AK1NrusAglrvV-SAXT0c1ZiG3IndlKsu5ltYHKCBPe9lAUm-0SCs-jhEpH6bZMIHV_m4PT9KTPh_vWoXDNRd0lg5oMKiGUuaYnVVi0e8Nq2F6djrKRb-f42KR5eL0AH6DDhsK5OLCKcNaRh1P-RQFhYuuqsixkC42gbfySMgvvWe4nneh7cKlFW_HXFt737VRkldsakgqDHRpRdeQ4URvx-8cS9s5Qd8727UzXM-osW7zTqUzXF9oK-6VqXm5tjE_e6zfa_HG2aVaqLCLnpGraW5m1tS2fNqz5zjnUt7ZksK39lFS-FUZaR-mvAz-Wzua8gx538bWBGf1dh0EjTV6r8TE1MoQz9zeQ5E9_g0|



\## Задача 1

Запрос: ошибки payments дольше 500 мс, от свежих к старым.

Сервер прочитал 1200 документов, чтобы вернуть 33, потому что индекса под запрос нет:

он перебрал всю коллекцию (COLLSCAN), проверил фильтр у каждого документа и отсортировал результат в памяти.



\## Задача 2

ESR: E (равенство) — service, level; S (сортировка) — ts; R (диапазон) — duration\_ms.

Команда: db.events.createIndex({ service: 1, level: 1, ts: -1, duration\_ms: 1 })

Просмотрено документов стало в 36 раз меньше (1200 / 33).

Шаг SORT пропал: внутри каждой пары service + level записи индекса уже лежат в порядке ts,

серверу не нужно сортировать результат отдельно.



\## Задача 3

Вариант А (диапазон впереди): 378 ключей. Первое поле — диапазон duration\_ms > 500,

сервер проходит весь участок индекса «дольше 500 мс», а там события всех сервисов и уровней;

подходят под payments и error только 33. SORT остался.

Вариант Б (диапазон перед сортировкой): 33 ключа, но SORT остался: поле ts стоит после диапазона,

внутри участка, отобранного диапазоном, порядок по ts не сохраняется.

Вывод: в рабочей базе оставила бы индекс по ESR (задача 2). У Б ключей меньше, но сортировка идёт в памяти,

а она ограничена 100 МБ и на большом журнале может завершиться ошибкой.



\## Задача 4

Запрос: level = "error", sort duration\_ms -1, limit 10.

ESR: равенство — level, сортировки — duration\_ms, диапазона нет, поэтому индекс из двух полей.

Команда: db.events.createIndex({ level: 1, duration\_ms: -1 })

В индексе записи со значением "error" лежат одним участком, уже отсортированным по duration\_ms

от большего к меньшему. Сервер встаёт в начало участка и берёт первые 10 записей, затем LIMIT

останавливает чтение, поэтому просмотрено 10 документов, а не все 180 ошибок.



\## Ответы на вопросы

\- totalKeysExamined — сколько записей индекса просмотрено, totalDocsExamined — сколько документов прочитано из коллекции.

\- FETCH нужен, потому что индекс хранит только значения индексируемых полей и ссылку на документ;

&#x20; чтобы вернуть документ целиком (route, status, trace и т. д.), сервер достаёт его из коллекции.

\- В задаче 2 просмотрено 43 ключа, а документов 33: в индексе под payments + error лежит 43 записи,

&#x20; а условие duration\_ms > 500 проверяется уже внутри этого участка, и 10 записей не подошли.

\- При вставке новой записи в журнал сервер добавляет запись и в индекс, на нужное место; запись чуть дольше.

\- Индексы на все поля не ставят: каждый индекс занимает место и замедляет вставку и обновление,

&#x20; а пользу приносит только запросам, под которые он построен.

