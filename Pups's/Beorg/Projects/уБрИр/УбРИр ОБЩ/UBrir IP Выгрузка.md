\\Srvmain\Производственный отдел\Информация\Количество выгруженных анкет
- СНИЛС
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB02'
    AND JSON_EXTRACT(FinalizedData, '$.other_snils') <> ''
    GROUP BY 1
    ```
    
- Анкета
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024) and
     CampaignID in ('20UB01', '20UB06', '20UB07', '20UB08', '20UB11', '20UB12', '20UB13')
    GROUP BY 1
    ```
    
- Паспорт
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB02'
    AND (JSON_EXTRACT(FinalizedData, '$.Number') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.Series') <> '' or
    JSON_EXTRACT(FinalizedData, '$.LastName') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.FirstName') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.MiddleName') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.BirthDate') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.BirthPlace') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.Gender') <> '') 
    GROUP BY 1
    ```
    
- ТК
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB03'
    GROUP BY 1
    ```
    
- 2НДФЛ
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB04'
     AND JSON_EXTRACT(FinalizedData, '$.type_ref') <> '' 
    GROUP BY 1
    ```
    
- СОПД
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 3 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB05'
     and (JSON_EXTRACT(FinalizedData, '$.LASTNAME') <> '' or 
    JSON_EXTRACT(FinalizedData, '$.FIRSTNAME') <> '' or
    JSON_EXTRACT(FinalizedData, '$.MIDDLENAME') <> ''or
    JSON_EXTRACT(FinalizedData, '$.claim_bkiSend') <> ''or
    JSON_EXTRACT(FinalizedData, '$.claim_bkiSendDate') <> '') 
    GROUP BY 1
    ```
    
- Кол-во Комплектов
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 02 and YEAR(Date) = 2024)
    GROUP BY 1
    ```
    
- 3-ий разворот паспорта
    ```sql
    SELECT * from ClientClusterUB.QuestionaryFields qf 
    where `DateTime` between '2024-02-01 00:00:00.0' and '2024-02-28 23:59:59.9'
    and Name = 'issued_passports_serial~~1'
    and NormalizedValue is not NULL 
    ```
    
- ПФР
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 2 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB10'
     AND JSON_EXTRACT(FinalizedData, '$.FIRSTNAME') <> '' 
    GROUP BY 1
    ```
    
- Справка об инвалидности
    ```sql
    select packID, count(*) from ClientClusterUB.Questionaries q
    where PackID in (
    select ID from ClientClusterUB.Sets s
    where MONTH(Date) = 03 and YEAR(Date) = 2024)
    and
     CampaignID = '20UB16'
    GROUP BY 1
    ```
    
- Сортировка
    ```sql
    SELECT CampaignID,
    CASE CampaignID
      WHEN '20UB01' THEN 'Анкета'
      WHEN '20UB02' THEN 'Паспорт РФ/СНИЛС'
      WHEN '20UB03' THEN 'Трудовая книжка'
      WHEN '20UB04' THEN 'Справка о доходах'
      WHEN '20UB05' THEN 'СОПД'
      WHEN '20UB06' THEN 'Анкета Этажи короткая'
      WHEN '20UB07' THEN 'Анкета Этажи полная'
      WHEN '20UB08' THEN 'Анкета ВТБ'
      WHEN '20UB09' THEN 'Согласие БКИ'
      WHEN '20UB10' THEN 'Выписка ПФР'
      WHEN '20UB11' THEN 'Анкета Цифровая ипотека'
      WHEN '20UB12' THEN 'Анкета Метр квадратный'
      WHEN '20UB13' THEN 'Анкета Промсвязьбанк'
      WHEN '20UB14' THEN 'Кредитный договор'
      WHEN '20UB15' THEN 'Свидетельство о рождении'
      WHEN '20UB16' THEN 'Справка об инвалидности'
      WHEN '20UB_anketa_brk' THEN 'Нетиповая анкета'
      WHEN '20UB_BRAK' THEN 'БРАК'
      ELSE 'Мастер'
      END 'DOC',
     COUNT(*) FROM ClientClusterUB.Questionaries WHERE Date BETWEEN '2024-03-01' AND  '2024-03-31' 
     and (OriginInfo like '%donor%' or OriginInfo is NULL)
     and campaignid != '20UB00'
    GROUP BY CampaignID
    ```