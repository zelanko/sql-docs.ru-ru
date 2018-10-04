---
title: Пример топологий и стоимости лицензирования для самостоятельной бизнес-аналитики SQL Server 2014 | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 682b8711-407a-48d1-9807-415d4c24dad6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 56e290ef8bf680f44ee11ec2e8d918b7b1d22c76
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091404"
---
# <a name="example-license-topologies-and-costs--for-sql-server-2014-self-service-business-intelligence"></a>Примеры топологий и стоимости лицензирования для самостоятельной бизнес-аналитики SQL Server 2014
  В этом разделе описаны рекомендации по выбору [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Business Intelligence edition или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition. В данный раздел включено несколько примеров локальных топологий самостоятельной бизнес-аналитики (BI) Майкрософт. Примеры содержат выпуски и лицензии, которые можно использовать для оптимизации баланса между производительностью и ценой. Топологии, количество серверов и стоимость лицензирования приведены **только в качестве примеров**. В Microsoft [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и Microsoft SharePoint 2013 внесены несколько изменений лицензирования, которые предоставляют дополнительные возможности для лицензирования серверов, пользователей и устройств. Лицензии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживают те же сценарии использования, связанные с бизнес-аналитикой.  
  
-   [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] доступен в выпуске Business Intelligence и предлагает лицензирование «на ядро» для некоторых выпусков [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   В SharePoint 2013 упрощено лицензирование для сценариев экстрасети или Интернета, а также варианты лицензирования SharePoint Online.  
  
 Перед покупкой изучите раздел «Инструкции по покупке» для каждого продукта и проконсультируйтесь с представителем Microsoft или локальным торговым посредником относительно конкретных требований лицензирования. Последние планы и цены использования лицензий см. на следующих ресурсах:  
  
-   [О лицензировании — SQL Server 2014](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx)  
  
-   [Лицензирование SharePoint 2013](http://office.microsoft.com/sharepoint/sharepoint-licensing-overview-collaboration-software-FX103789438.aspx).  
  
 **В этом разделе:**  
  
-   [Компоненты SQL Server Business Intelligence](#bkmk_bi_components)  
  
-   [Сводка лицензирования SQL Server 2014](#bkmk_sql_server_license)  
  
-   [Сводная информация по лицензированию SharePoint 2013](#bkmk_sharepoint_license)  
  
-   [Трехуровневая топология с отдельными серверами PowerPivot](#bkmk_3tier_powerpivot)  
  
-   [Трехуровневая топология](#bkmk_3tier)  
  
-   [Двухуровневая топология](#bkmk_2tier)  
  
-   [Ссылки и материалы сообщества](#bkmk_reference)  
  
##  <a name="bkmk_bi_components"></a> Компоненты SQL Server Business Intelligence  
 В этом разделе рассматриваются серверные технологии SQL Server и SharePoint. Стоимость и примеры не обязательно демонстрируют компоненты Microsoft Windows Server или Microsoft Office, которые требуются вам для получения полнофункционального клиентского и серверного решения. В этом разделе рассматриваются следующие компоненты SQL Server Business Intelligence: службы SQL Server Reporting Services, работающие в режиме интеграции с SharePoint, и надстройка PowerPivot для SharePoint. Данные компоненты предоставляют следующие возможности:  
  
-   интерактивные книги PowerPivot в браузере;  
  
-   Интерактивные [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] отчетов в SharePoint.  
  
-   Коллекция [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)], обновление данных по расписанию, панель управления.  
  
-   службы Reporting Services в режиме интеграции с SharePoint, включая предупреждения об изменении данных.  
  
 Дополнительные сведения см. в таблице возможностях [Установка компонентов SQL Server BI с SharePoint &#40;PowerPivot и служб Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="license-summary"></a>Сводные данные о лицензировании  
 В этом разделе представлена сводная информация о требованиях лицензирования для SQL Server и SharePoint. Это информация высокого уровня, охватывающая только сценарии, используемые в диаграммах топологии и примерах, приведенных в данном документе. Для получения дополнительных сведений ознакомьтесь с представленными ссылками. Цены в примерах основаны на ценах программы Microsoft Open License Program (MOLP).  
  
 Распространенной практикой является использование **Enterprise Edition** для серверов, на которых запущен компонент SQL Server Database Engine, и **Business Intelligence** для серверов, на которых работают службы Reporting Services или надстройка PowerPivot для SharePoint. Однако **число пользователей** и **количество ядер ЦП сервера** в развертывании влияют на затраты и решение о выборе выпуска, который нужно использовать.  
  
###  <a name="bkmk_sql_server_license"></a> Сводка лицензирования SQL Server 2014  
  
-   Для SQL Server Enterprise Edition используется лицензирование «на ядро». Лицензии «на ядро» продаются в пакетах на **два ядра** .  
  
-   Выпуск SQL Server BI использует серверные лицензии и клиентские лицензии (CAL).  
  
-   Соглашения CAL основаны на каждом пользователе или устройстве, подключенном к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], независимо от числа серверов, к которым они подключаются.  
  
-   При лицензировании «на ядро» требуется, чтобы все ядра сервера охватывались лицензией. Для каждого физического процессора на сервере применяется требование: минимум **4** лицензии «на ядро».  
  
 В следующей таблице представлена сводная информация о лицензиях, используемых для проектирования развертывания и оценки стоимости лицензирования. **ПРИМЕЧАНИЕ.**  Цены показаны только в качестве примера.  
  
|Выпуски SQL Server|Лицензия SQL Server + клиентская лицензия (CAL)|Лицензии SQL Server «на ядро»|  
|-------------------------|---------------------------------------------------------|-----------------------------------|  
|Enterprise|Неприменимо|**(Да)** $6874 X [число ядер] X [коэффициент ядра]|  
|Business Intelligence|**(Да)** $8592 + $199 на CAL|Неприменимо|  
|Standard|**(Да)**|**(Да)**|  
  
 Дополнительные сведения об образце [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] цен лицензий, см. в разделе:  
  
-   [Лицензирование для виртуальных сред](http://www.microsoft.com/licensing/about-licensing/virtualization.aspx) (http://www.microsoft.com/licensing/about-licensing/virtualization.aspx).  
  
-   [SQL Server 2014 таблица лицензирования — Главная страница Microsoft](http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (http://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Выпуски SQL server 2014 и лицензирование](http://www.microsoft.com/licensing/about-licensing/sql2014.aspx#tab=2)  
  
1.  **Предположения SQL Server и Дополнительные сведения о лицензировании:**  
  
2.  В диаграммах в данном разделе используется выпуск SQL Server Enterprise Edition для серверов базы данных, поэтому доступен полный набор функций высокой доступности, например группы доступности AlwaysOn. Дополнительные сведения см. в разделе [Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
3.  Все серверы в этом примере оснащены двумя 6-ядерными процессорами Intel Xeon, поэтому при вычислении стоимости лицензии применяется **коэффициент ядра SQL Server** , равный **1** . Дополнительные сведения об основных факторах и стоимости лицензирования см. в разделе [таблица основных факторов SQL Server](http://download.microsoft.com/download/9/B/F/9BF63163-D8F9-4339-90AA-EBC9AAFC49AD/SQL2012_CoreFactorTable_Mar2012.pdf) (http://download.microsoft.com/download/0/C/8/0C85665B-11EA-4FF5-B37C-8CC21CF95AC4/BizTalk%202013_CoreFactorTable_**3.19.2013**. v4.pdf).  
  
###  <a name="bkmk_sharepoint_license"></a> Сводная информация по лицензированию SharePoint 2013  
 В следующем списке представлена сводка по модели лицензирования, используемой для проектирования развертывания и оценки стоимости лицензирования. Цены показаны только в качестве примера.  
  
1.  Для каждого экземпляра Microsoft SharePoint Server требуется лицензия на сервере SharePoint.  
  
2.  Для лицензирования SharePoint Enterprise для каждого конечного пользователя или устройства необходимо приобрести **лицензию Standard CAL** для Microsoft SharePoint Server 2013, помимо **лицензии Enterprise CAL**.  
  
3.  Клиентские лицензии SharePoint приобретаются на одного пользователя или устройство, которые получают доступ к серверам SharePoint. Не нужно приобретать клиентские лицензии для каждого сервера.  
  
 Например, если ваша среда состоит из двух экземпляров, с которыми работают 100 пользователей, стоимость лицензий будет следующий:  
  
-   Лицензия Standard CAL для Microsoft SharePoint Server 2013: **107,99 долл. США**.  
  
-   Лицензия Enterprise CAL для Microsoft SharePoint Server 2013: **94,99 долл. США**.  
  
-   Лицензия Microsoft SharePoint Server 2013: **6412,99 долл. США**.  
  
 Стоимость: **33 123,98 долл. США**.  
  
-   Клиентская лицензия: (107,99 долл. США + 94,99 долл. США) X 100) =20 298,00 долл. США.  
  
-   Серверная лицензия: (6412,99 долл. США X 2) =12 825,98 долл. США.  
  
 **Предположения SharePoint и Дополнительные сведения о лицензировании:**  
  
 В примерах развертывания используются среды интрасети, поэтому необходимы клиентские лицензии SharePoint.  
  
-   [Полный список лицензий SharePoint](http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise) (http://technet.microsoft.com/en-in/library/jj819267.aspx#bkmk_FeaturesOnPremise).  
  
-   [Инструкции по покупке SharePoint](http://sharepoint.microsoft.com/en-in/Pages/buy.aspx) (http://sharepoint.microsoft.com/en-in/Pages/buy.aspx).  
  
##  <a name="bkmk_3tier_powerpivot"></a> Трехуровневая топология с отдельными [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] серверов  
 В этом примере показано, что при наличии 800 или меньшего числа пользователей наиболее экономичный вариант — использовать выпуск SQL Server BI для серверов приложений SharePoint и [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для серверов SharePoint. Однако, если число пользователей равно 800 или больше, выпуск SQL Server Enterprise Edition будет более экономичным. Лицензирование «на ядро» не зависит от числа пользователей, поэтому существует пороговое значение стоимости при сравнении лицензий «на ядро» и клиентских лицензий и увеличении числа пользователей. После превышения порогового значения Enterprise Edition становится наиболее экономичным решением. Чтобы определить пороговое значение, сравните затраты на основе количества лицензируемых ядер и число клиентских лицензий для конечных пользователей и устройств.  
  
-   В этом примере представлено развертывание в интрасети, поэтому для SharePoint 2013 требуются клиентские лицензии.  
  
-   Роль приложения (2) включает службы SQL Server Reporting Services в режиме интеграции с SharePoint.  
  
     Базы данных приложения службы SharePoint расположены на серверах роли базы данных (4).  
  
-   [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint выполняется на отдельных серверах (3). [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для SharePoint 2013 работает за пределами фермы SharePoint и может устанавливаться на серверах, которые не включают установку SharePoint, повышая производительность.  
  
-   Роль базы данных (4) использует SQL Server Enterprise, поэтому группы доступности AlwaysOn, компонент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], доступны.  
  
 ![bi_license_3tiers_and_ASseparate](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseparate.gif "bi_license_3tiers_and_ASseparate")  
  
 С 100 пользователями выпуск SQL Server BI более экономичен.  
  
 ![bi_license_3tiers_and_ASseperate_calcs](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs.gif "bi_license_3tiers_and_ASseperate_calcs")  
  
 Но при наличии 300 пользователей выпуск SQL Server Enterprise Edition становится более экономичным.  
  
 ![bi_license_3tiers_and_ASseperate_calcs2](../../../2014/sql-server/install/media/bi-license-3tiers-and-asseperate-calcs2.gif "bi_license_3tiers_and_ASseperate_calcs2")  
  
##  <a name="bkmk_3tier"></a> Трехуровневая топология  
 Этот пример показывает, что при наличии 100 или меньшего числа пользователей менее затратно использовать выпуск SQL BI для серверов с SQL Server BI. Однако, если число пользователей равно 500 или больше 500, выпуск SQL Server Enterprise Edition будет более экономичным.  
  
-   В этом примере представлено развертывание в интрасети, поэтому для SharePoint 2013 требуются клиентские лицензии.  
  
-   Службы Analysis Services в режиме PowerPivot (2) работают за пределами фермы, но PowerPivot работает **на тех же физических** серверах в другой роли приложения.  
  
-   Роль базы данных (3) использует SQL Server Enterprise, чтобы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функция групп доступности AlwaysOn доступна.  
  
 ![bi_license_3tiers](../../../2014/sql-server/install/media/bi-license-3tiers.gif "bi_license_3tiers")  
  
 С 100 пользователями выпуск SQL Server BI более экономичен.  
  
 ![bi_license_3tiers_calcs1](../../../2014/sql-server/install/media/bi-license-3tiers-calcs1.gif "bi_license_3tiers_calcs1")  
  
 Но при наличии 500 пользователей выпуск SQL Server Enterprise Edition становится более экономичным.  
  
 ![bi_license_3tiers_calcs3](../../../2014/sql-server/install/media/bi-license-3tiers-calcs3.gif "bi_license_3tiers_calcs3")  
  
##  <a name="bkmk_2tier"></a> Двухуровневая топология  
 При наличии только двух уровней используется SQL Server Enterprise Edition, чтобы группы доступности AlwaysOn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно было использовать для компонента SQL Server Database Engine. Поэтому различий в затратах между выпусками SQL Server нет. Единственная переменная — это цена клиентской лицензии SharePoint, зависящая от числа пользователей.  
  
-   В этом примере представлено развертывание в интрасети, поэтому для SharePoint 2013 требуются клиентские лицензии.  
  
-   Службы Analysis Services в режиме PowerPivot выполняются за пределами фермы, но PowerPivot работает на тех же физических серверах (2), что и компонент SQL Server Database Engine.  
  
 ![bi_license_2tiers](../../../2014/sql-server/install/media/bi-license-2tiers.gif "bi_license_2tiers")  
  
 ![bi_license_2tiers_calcs1](../../../2014/sql-server/install/media/bi-license-2tiers-calcs1.gif "bi_license_2tiers_calcs1")  
  
##  <a name="bkmk_reference"></a> Ссылки и материалы сообщества  
  
### <a name="license-tools"></a>Средства лицензирования  
  
-   [Microsoft License Advisor](http://mla.microsoft.com/default.aspx) (http://mla.microsoft.com/default.aspx).  
  
-   [Клиент средство Access License (CAL) Decision](http://www.microsoft.com/licensing/CalTool/) (http://www.microsoft.com/licensing/CalTool/).  
  
-   [Microsoft Business Hub: Инструкции по покупке](http://www.microsoftbusinesshub.com/How_To_Buy#) (http://www.microsoftbusinesshub.com/How_To_Buy#).  
  
### <a name="microsoft-license-information"></a>Сведения о лицензии Microsoft  
  
-   [О лицензировании: Клиентские лицензии и лицензии управления](http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx) (http://www.microsoft.com/licensing/about-licensing/client-access-license.aspx).  
  
-   [О лицензировании: Поиск лицензий продуктов](http://www.microsoftvolumelicensing.com/default.aspx) (http://www.microsoftvolumelicensing.com/default.aspx).  
  
-   [Корпоративного лицензирования: цены и инструкции по покупке](http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx) (http://www.microsoft.com/licensing/how-to-buy/how-to-buy.aspx).  
  
### <a name="community-content"></a>Содержимое сообщества  
  
-   [Лицензирование SQL Server 2014 Developer Edition](http://sqlmag.com/sql-server-2014/sql-server-2014-developer-edition-licensing).  
  
-   [Изменения лицензирования SQL Server 2014](http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes)(http://www.brentozar.com/archive/2014/04/sql-server-2014-licensing-changes).  
  
-   [Изменения в лицензировании SQL Server 2014](https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf)(https://www.directionsonmicrosoft.com/sites/default/files/PDFs/Licensing_Changes_for_SQL_Server_2014.pdf).  
  
-   [Оценка SharePoint 2013, затраты на Лицензирование](http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/) (http://www.degdigital.com/blog/sharepoint-2013-licensing-for-dummies/).  
  
-   [Microsoft сообщество клиентов корпоративного лицензирования](http://www.microsoft.com/licensing/existing-customers/community.aspx) (http://www.microsoft.com/licensing/existing-customers/community.aspx).  
  
  
