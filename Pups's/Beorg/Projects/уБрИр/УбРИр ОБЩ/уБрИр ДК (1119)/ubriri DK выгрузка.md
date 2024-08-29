- Проекты (менять номер)
    ```sql
    select packID, count(*) from ClientClusterUBRD.Questionaries q
    where PackID in (
    select ID from ClientClusterUBRD.Sets s
    where MONTH(Date) = 2 and YEAR(Date) = 2024)
    and
     CampaignID = '23UBRD01'
    GROUP BY 1
    ```
    
- Кол-во страниц
    ```sql
    SELECT CampaignID,
    CASE CampaignID
      WHEN '23UBRD01' THEN 'Паспорт'
      WHEN '23UBRD02' THEN 'Анкета-заявление'
      WHEN '23UBRD03' THEN 'ЗПП КБО/доп.согл к ДКБО'
      WHEN '23UBRD04' THEN 'Опросный лист CRS'
      WHEN '23UBRD05' THEN 'Опросный лист FATCA'
      WHEN '23UBRD06' THEN 'Заявление на изменение ПД'
      WHEN '23UBRD07' THEN 'Фото клиента с картой'
      WHEN '23UBRD08' THEN 'Пин-конверт'
      WHEN '23UBRD_NT' THEN 'Нетиповые документы'
      ELSE 'Мастер'
      END 'DOC',
     COUNT(*) FROM ClientClusterUBRD.Questionaries WHERE Date BETWEEN '2024-03-01' AND  '2024-03-31' 
     and (OriginInfo like '%donor%' or OriginInfo is NULL)
    GROUP BY CampaignID;
    ```
    
- Кол-во комплектов
    ```sql
    select packID, count(*) from ClientClusterUBRD.Questionaries q
    where PackID in (
    select ID from ClientClusterUBRD.Sets s
    where MONTH(Date) = 2 and YEAR(Date) = 2024)
    GROUP BY 1
    ```
    
- По дням
    ```sql
    select packID, count(*) from ClientClusterUBRD.Questionaries q
    where PackID in (
    select ID from ClientClusterUBRD.Sets s
    where DAYOFMONTH(Date) >= 11 and MONTH(Date) = 12 and YEAR(Date) = 2023)
    and
     CampaignID = '23UBRD08'
    GROUP BY 1
    ```