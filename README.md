# hak_CP_FINAL_SBER_2020_KeyIdea

#ФИЧА 1: Агрегация текстовых сообщений в группы по смыслу (тематическое моделирование)
hak_CP_FINAL_SBER_2020_KeyIdea/data_analysis/groupMessagesLDA.ipynb

 - стандартный nlp-pipeline текстовой предобработки (очистка сообщений от лишней разметки, выделение отдельных слов, лемматизация, стемминг, приведение к нормальной форме, удаление стоп-слов)
 - составление n-gram (для захвата локального контекста)
 - алгоритм LDA применяется к пулу входяших/исходящих сообщений inbox.json/outbox.json
 - отрисовка WordCloud для визуализации состава тематики и корректного нейминга
 
 
#ФИЧА 2: Суммаризация текстовых сообщений (длинный текст -> короткий текст)
hak_CP_FINAL_SBER_2020_KeyIdea/backend_microservices/textSummarizatiopnGPT.ipynb

 - абстрактивная суммаризация (от изначального текста берется порядка 10%, остальное "дописывает" модель, результирующий текст с учетом дописанного моделью "хвоста" короче изначального сообщения)
 - flask сервис с предобученным GPT от SberDevices и SberAI (https://github.com/sberbank-ai/ru-gpts)
 
 
#ФИЧА 3: Голосовой помощник (по типу Яндекс.Алиса, СберСалют и т.д.)
hak_CP_FINAL_SBER_2020_KeyIdea/backend_microservices/keyIdeaTelebot.ipynb

 - реализован полный цикл работы с голосом (text_to_speech+speech_to_text)
   - text_to_speech: сообщения читаются помощником, предлагает действия исходя из текущего контекста
   - speech_to_text: голосовой ассистент распознает голосовые команды и умеет выполнять как простые действия (удалить сообщене, пометить как прочитанное), так и целые сценарии (делегирование задачи + приложенный)

 - использование технологий Yandex.SpeechKit (https://cloud.yandex.ru/docs/speechkit/quickstart)
 - для запуска нелобходимо добавить:
   - API_TOKEN telegram (https://tlgrm.ru/docs/bots/api)
   - IAM_TOKEN yandex (https://cloud.yandex.ru/docs/iam/operations/iam-token/create)
   - FOLDER_ID yandex (идентификатор каталога Yandex.Cloud)
 - в папке hak_CP_FINAL_SBER_2020_KeyIdea/backend_microservices/speech.zip содержатся звуковые файлы в формате .ogg (подробнее про формат аудио для Yandex.SpeechKit можно прочитать тут: https://cloud.yandex.ru/docs/speechkit/stt/formats)
 - в рамках демонстрации работы прототипа голосового помощника был создан telegram-бот @Sberbank_Digital_Manager_bot, telegram "бесшовно" интегрируется с Yandex.SpeechKit в части работы со звуком (не требуется дополнительного перекодирования аудиодорожек)
 - в данным момент бот контактирует только с его разработчиком (@lividhour), прочие сообщения фильтруются

Если вы хотите получить доступ к чатботу, свяжитесь с контактными лицами от команды:

- Васичкин Евгений
@lividhour
+79296224635

- Юсупов Егор
@EgorYusupov
+79227080712

- Семенов Викентий
@hokknok
+79164748883
