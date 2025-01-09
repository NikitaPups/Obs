## Проекты: 
```
  select packID, count(*) from ClientClusterVLS.Questionaries q
    where PackID in (
    select ID from ClientClusterVLS.Sets s
    where MONTH(Date) = 12 and YEAR(Date) = 2024)
    and
     CampaignID = '24VLS_PSS'
    GROUP BY 1
```
## Кол-во комплектов:
```
 select packID, count(*) from ClientClusterVLS.Questionaries q
    where PackID in (
    select ID from ClientClusterVLS.Sets s
    where MONTH(Date) = 2 and YEAR(Date) = 2024)
    GROUP BY 1
```
## Сортировка:
```
   SELECT CampaignID,
    CASE CampaignID
      WHEN '24VLS_PSS' THEN 'Паспорт'
      WHEN '24VLS_SNILS' THEN 'СНИЛС'
      WHEN '24VLS_INN' THEN 'ИНН'
      WHEN '24VLS_VNB' THEN 'ВОЕННЫЙ БИЛЕТ'
      WHEN '24VLS_TK' THEN 'ТРУДОВАЯ КНИЖК/СТД-Р/СЗВ-ТД'
      WHEN '24VLS_DOO' THEN 'ДОКУМЕНТЫ ОБ ОБРАЗОВАНИИ'
      WHEN '24VLS_SOOS' THEN 'СПРАВКА ОБ ОТСУТСТВИИ СУДИМОСТИ'
      WHEN '24VLS_BRK' THEN 'Нетиповые документы'
      ELSE 'Мастер'
      END 'DOC',
     COUNT(*) FROM ClientClusterVLS.Questionaries WHERE Date BETWEEN '2024-12-01' AND  '2024-12-31' 
     and (OriginInfo like '%donor%' or OriginInfo is NULL)
    GROUP BY CampaignID;
```

