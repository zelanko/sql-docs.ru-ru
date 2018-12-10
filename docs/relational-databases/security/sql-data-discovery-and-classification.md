---
title: Обнаружение и классификация данных SQL | Документы Майкрософт
description: Обнаружение и классификация данных SQL
documentationcenter: ''
ms.reviewer: carlrab
ms.assetid: 89c2a155-c2fb-4b67-bc19-9b4e03c6d3bc
ms.service: sql-database
ms.prod_service: sql-database,sql
ms.custom: security
ms.topic: conceptual
ms.date: 02/13/2018
ms.author: giladm
author: giladm
manager: shaik
ms.openlocfilehash: 18495f81289981d4ce5a72ac943150bfea4c4f3d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52539132"
---
# <a name="sql-data-discovery-and-classification"></a>Обнаружение и классификация данных SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Обнаружение и классификация данных — это новое средство, встроенное в SQL Server Management Studio (SSMS), для **обнаружения**, **классификации**, **пометки** &  и **создания отчетов** о конфиденциальных данных в базах данных.
Обнаружение и классификация наиболее важных данных (деловых, финансовых, персональных и т. д.) может играть ключевую роль в защите информации в вашей организации. На основе этих процессов может формироваться инфраструктура для решения следующих задач:
* соблюдение стандартов конфиденциальности данных;
* управление доступом к базам данных и столбцам, содержащим конфиденциальные данные, а также усиление их безопасности.

> [!NOTE]
> Средство обнаружения и классификации данных **поддерживается в SQL Server 2008 и более поздних версиях**. Сведения, касающиеся Базы данных SQL Azure, см. в статье [Обнаружение и классификация данных в Базе данных SQL Azure](https://go.microsoft.com/fwlink/?linkid=866265).

## <a id="subheading-1"></a>Обзор
Средство обнаружения и классификации данных включает в себя набор эффективных служб, которые образуют новую парадигму SQL Information Protection, направленную на защиту данных, а не только базы данных.
* **Обнаружение и рекомендации**. Подсистема классификации проверяет базу данных и определяет столбцы, содержащие потенциально конфиденциальные данные. Затем вы можете легко просмотреть и применить рекомендации по классификации, а также классифицировать столбцы вручную.
* **Метки**. Столбцам можно назначать постоянные метки классификации конфиденциальных данных.
* **Видимость**. Состояние классификации базы данных можно просматривать в подробном отчете, который можно напечатать или экспортировать для использования в целях соблюдения требований или аудита, а также в других целях.

## <a id="subheading-2"></a>Обнаружение, классификация конфиденциальных столбцов и назначение им меток
В следующем разделе описываются действия по обнаружению в базе данных столбцов, содержащих конфиденциальные данные, их классификации и назначению им меток, а также просмотру текущего состояния классификации базы данных и экспорту отчетов.

Классификация включает в себя два типа атрибутов метаданных:
* метки — основные атрибуты классификации, которые служат для определения уровня конфиденциальности данных, хранящихся в столбце;  
* типы сведений — предоставляют более подробные сведения о типе данных, хранящихся в столбце.

<br>
**Классификация базы данных SQL Server**

1. В SQL Server Management Studio (SSMS) подключитесь к серверу SQL Server.

2. В обозревателе объектов SSMS щелкните правой кнопкой мыши базу данных, которую необходимо классифицировать, и выберите пункты **Задачи** > **Классифицировать данные...**.

    ![Область навигации][1]

3. Подсистема классификации ищет в базе данных столбцы с потенциально конфиденциальными данными и предоставляет список **рекомендованных классификаций столбцов**.

    * Чтобы просмотреть список рекомендованных классификаций столбцов, щелкните поле уведомления о рекомендациях в верхней части окна или панель рекомендаций в его нижней части.

        ![Область навигации][2]

        ![Область навигации][3]

    * Просмотрите список рекомендаций.
        * Чтобы применить рекомендацию для определенного столбца, установите флажок в левом поле соответствующей строки. Вы также можете принять *все рекомендации*, установив флажок в заголовке таблицы рекомендаций.

        * Кроме того, вы можете изменить рекомендованные тип сведений и метку конфиденциальности с помощью полей с раскрывающимися списками.        

        ![Область навигации][4]

    * Чтобы применить выбранные рекомендации, нажмите синюю кнопку **Принять выбранные рекомендации**.

        ![Область навигации][5]

4. Вы также можете **классифицировать столбцы вручную** вместо использования рекомендованных классификаций или в дополнение к ним.

    * В меню в верхней части страницы щелкните **Добавить классификацию**.

        ![Область навигации][6]

    * В открывшемся контекстном окне выберите схему, таблицу и столбец, которые нужно классифицировать, а затем выберите тип сведений и метку классификации. После этого нажмите синюю кнопку **Добавить классификацию** в нижней части контекстного окна.

        ![Область навигации][7]

5. Чтобы завершить классификацию и назначить столбцам базы данных новые метаданные (метки) классификации, щелкните элемент **Сохранить** в меню в верхней части окна.

    ![Область навигации][8]


6. Чтобы создать отчет с полной сводкой состояния классификации базы данных, в меню в верхней части окна щелкните **Просмотреть отчет**.

    ![Область навигации][9]

    ![Область навигации][10]


## <a id="subheading-3"></a>Доступ к метаданным классификации

Метаданные классификации для *типов сведений* и *меток конфиденциальности* хранятся в следующих расширенных свойствах: 
* sys_information_type_name;
* sys_sensitivity_label_name.

Доступ к метаданным осуществляется с помощью представления каталога расширенных свойств [sys.extended_properties](https://docs.microsoft.com/sql/relational-databases/system-catalog-views/extended-properties-catalog-views-sys-extended-properties).

В следующем примере кода возвращаются все классифицированные столбцы с их соответствующими классификациями.

```sql
SELECT
    schema_name(O.schema_id) AS schema_name,
    O.NAME AS table_name,
    C.NAME AS column_name,
    information_type,
    sensitivity_label 
FROM
    (
        SELECT
            IT.major_id,
            IT.minor_id,
            IT.information_type,
            L.sensitivity_label 
        FROM
        (
            SELECT
                major_id,
                minor_id,
                value AS information_type 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_information_type_name'
        ) IT 
        FULL OUTER JOIN
        (
            SELECT
                major_id,
                minor_id,
                value AS sensitivity_label 
            FROM sys.extended_properties 
            WHERE NAME = 'sys_sensitivity_label_name'
        ) L 
        ON IT.major_id = L.major_id AND IT.minor_id = L.minor_id
    ) EP
    JOIN sys.objects O
    ON  EP.major_id = O.object_id 
    JOIN sys.columns C 
    ON  EP.major_id = C.object_id AND EP.minor_id = C.column_id
```

## <a id="subheading-4"></a>Следующие шаги

Сведения, касающиеся Базы данных SQL Azure, см. в статье [Обнаружение и классификация данных в Базе данных SQL Azure](https://go.microsoft.com/fwlink/?linkid=866265).

Рекомендуем защитить конфиденциальные столбцы путем применения механизмов защиты на уровне столбцов:

* [динамическое маскирование данных](https://docs.microsoft.com/sql/relational-databases/security/dynamic-data-masking) для затемнения конфиденциальных столбцов в процессе использования;
* [Always Encrypted](https://docs.microsoft.com/sql/relational-databases/security/encryption/always-encrypted-database-engine) для шифрования конфиденциальных столбцов в процессе хранения.

<!--Anchors-->
[SQL Data Discovery & Classification overview]: #subheading-1
[Discovering, classifying & labeling sensitive columns]: #subheading-2
[Accessing the classification metadata]: #subheading-3
[Next Steps]: #subheading-4

<!--Image references-->
[1]: ./media/sql-data-discovery-and-classification/1_data_classification_explorer_menu.png
[2]: ./media/sql-data-discovery-and-classification/2_recommendations_notification_box.png
[3]: ./media/sql-data-discovery-and-classification/3_recommendations_panel.png
[4]: ./media/sql-data-discovery-and-classification/4_recommendations.png
[5]: ./media/sql-data-discovery-and-classification/5_accept_recommendations_button.png
[6]: ./media/sql-data-discovery-and-classification/6_add_classification_button.png
[7]: ./media/sql-data-discovery-and-classification/7_manual_classification.png
[8]: ./media/sql-data-discovery-and-classification/8_save.png
[9]: ./media/sql-data-discovery-and-classification/9_view_report.png
[10]: ./media/sql-data-discovery-and-classification/10_report.png
