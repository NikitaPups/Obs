Добрый день!
Поправили контура. Теперь паспортный контур до 10 секунд. Для загрузки в него такие настройки :
POST: https://api.beorg.ru/api/bescan/add_document
{
  "token": "f4c454d962093ae76fcc219ae07d0193", 
  "machine_uid": "B9WXY56FYF6CKWRKEMYG5QJR8YJYJ2E4OP3FDIQK",
  "project_id": "24AVSL_PSS",
  "images": ["somestringencodedinbase64"]
}
GET: https://api.beorg.ru/api/document/result/NUMBER?token=TOKEN
Где NUMBER - номер загруженного документа, TOKEN - Выданный вам токен 

А второй контур с "заграничным паспортом", "свидетельством о рождении" и "иностранным паспортом". 
В него загрузка будет происходит по ранее выданным доступам:
POST:https://api.beorg.ru/api/bescan/add_document
{
  "token": "e078752702c316c0aac695dcfb61095e", 
  "machine_uid": "FYWVBP14TNYP4XCEGJC0KXVY9RCU6HCAUNJVXMWQ",
  "project_id": "24AVSL_MAST",
  "images": ["somestringencodedinbase64"]
}
GET: https://api.beorg.ru/api/document/result/s-NUMBER?token=TOKEN
Где NUMBER - номер загруженного комплекта документов, TOKEN - Выданный вам токен 

Вывод оставил в обоих случаях одинаковый, просто незаполненные поля будут приходит пустыми на обоих контурах