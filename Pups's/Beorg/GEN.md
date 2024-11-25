
| УБРиРИ      | [[УбРиР Общ.]]        | 1023/1119 |
| ----------- | --------------------- | --------- |
| Велес-строй | [[Veles]]             | 1147      |
| AviaSales   | [[Aviasales General]] | 1148      |
| RedOcean    | [[ЗакрытиЁ]]          | 1124      |
| Мега-хит    | [[Мага-хит]]          | 1158      |
| Ямми груп   | [[Таблица]]           | 1162      |
| НИОПИК      | [[Общ.]]              | 1161      |
| Общее       | [[Общее]]             |           |
Шаблоны договоров: \\vps-rhs.beorg.local\Шаблоны документов_ new_ 2023

=ТЕКСТ.СЦЕПИТЬ(ЕСЛИ(_24SBRNK_ARCH_22_11_2024[@DEVELOPER]<>"";_24SBRNK_ARCH_22_11_2024[@DEVELOPER];"");
               ЕСЛИ(И(_24SBRNK_ARCH_22_11_2024[@DEVELOPER]<>"";_24SBRNK_ARCH_22_11_2024[@[INVENTORY_NUMBER]]<>"");"_";""); ЕСЛИ(_24SBRNK_ARCH_22_11_2024[@[INVENTORY_NUMBER]]<>"";_24SBRNK_ARCH_22_11_2024[@[INVENTORY_NUMBER]];"");
               ЕСЛИ(И(_24SBRNK_ARCH_22_11_2024[@[INVENTORY_NUMBER]]<>"";_24SBRNK_ARCH_22_11_2024[@[DOC_TYPE]]<>"");"_";""); ЕСЛИ(_24SBRNK_ARCH_22_11_2024[@[DOC_TYPE]]<>"";_24SBRNK_ARCH_22_11_2024[@[DOC_TYPE]];"");
               ЕСЛИ(И(_24SBRNK_ARCH_22_11_2024[@[DOC_TYPE]]<>"";_24SBRNK_ARCH_22_11_2024[@[DOC_NAME]]<>"");"_";""); ЕСЛИ(_24SBRNK_ARCH_22_11_2024[@[DOC_NAME]]<>"";_24SBRNK_ARCH_22_11_2024[@[DOC_NAME]];"");
               ЕСЛИ(И(_24SBRNK_ARCH_22_11_2024[@DEVELOPER]<>"";_24SBRNK_ARCH_22_11_2024[@[SHEETS_NUM]]<>"");"_";""); ЕСЛИ(_24SBRNK_ARCH_22_11_2024[@[SHEETS_NUM]]<>"";_24SBRNK_ARCH_22_11_2024[@[SHEETS_NUM]];""))