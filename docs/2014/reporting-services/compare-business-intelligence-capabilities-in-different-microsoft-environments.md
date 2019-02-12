---
title: Сравните возможности бизнес-аналитики в разных средах Microsoft | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 1fb759ee-8172-4c4c-9f7d-49af2c731006
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 4f4339b91573aad752460b71fb4cce2181c9b880
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56018166"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Сравнение возможностей бизнес-аналитики в разных средах Microsoft
  Средства бизнес-аналитики Майкрософт [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] могут развертываться в нескольких различных средах, в том числе [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с SharePoint Server, SharePoint Online и Power BI для Office 365. В этом разделе приводится сравнение компонентов и функций, поддерживаемых в каждой среде.  
  
 Дополнительные сведения о сравнении SharePoint Server и SharePoint Online см. в разделе [Сравнение планов и параметров SharePoint](http://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Создание и управление отчетами бизнес-аналитики и панелями мониторинга  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online план 2|Power BI для Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Узлы бизнес-аналитики|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]Коллекции|Нет|Сайт Power BI|  
|Центральное управление данными, совместное использование запросов и управление ими|Нет|Нет|Да **<sup>1</sup>**|  
|Интеграция с Master Data Services (MDS) и Data Quality Services (DQS)|Да|Нет|Нет|  
|Расписание обновления данных|Да, но не поддерживает рабочие книги, содержащие данные Power Query|Нет|Да|  
|Запрос на естественном языке (вопросы и ответы)|Нет|Нет|Да **<sup>2</sup>**|  
|Предсказуемое прогнозирование|Нет|Нет|Да **<sup>3</sup>**|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] интеграция|Да|Нет|Нет|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Интеграция (многомерные и табличные данные)|Да|Нет|Нет|  
|Экспорт интерактивных панелей мониторинга Power View в презентацию PowerPoint|Да|Нет|Нет|  
|Создание панели мониторинга в браузере|Да|Нет|Нет|  
|Отслеживание использования|Да|Нет|Да|  
|Использование безопасности на основе строк кубов [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Да|Нет|Нет|  
  
 **<sup>1</sup>**[основные сведения о роли управляющих данными в управлении данными](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) и [видео: Power BI управлении информацией и администраторе данных](https://www.youtube.com/watch?v=8dHOj68ts7c).  
  
 **<sup>2</sup>**[power BI Q & A: Оптимизация рабочей книги Power BI (Облачное моделирование)](https://support.office.com/article/Power-BI-Q-A-Optimize-a-Power-BI-workbook-cloud-modeling--96dc5941-d0f1-44e2-9d9d-c038a3a55849?ui=en-US&rs=en-US&ad=US).  
  
 **<sup>3</sup>**[Знакомство с новыми возможностями прогнозирования в Power View для Office 365](https://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).  
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Просмотр и обзор данных, отчетов и панелей мониторинга бизнес-аналитики  
  
||SQL Server 2014 и SharePoint Server 2013|SharePoint Online план 2|Power BI для Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Просмотр рабочих книг Microsoft Excel в браузере|Да, если размер рабочей книги меньше, чем 2 ГБ|Да, если размер рабочей книги меньше, чем 10 ГБ|Да, если размер рабочей книги меньше, чем 250 МБ|  
|Просмотр данных в браузере в HTML5|Нет|Нет|Да|  
|Приложения бизнес-аналитики для удаленного доступа к отчетам и панелям мониторинга|Нет|Нет|Да **<sup>1</sup>**|  
|Книга Excel с [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] в качестве источника данных **<sup>2</sup>**|Да|Нет|Нет|  
|Возможность использования функций в различных браузерах и версиях|Да, для визуализации не в Power View **<sup>3</sup>**|Да, для файлов рабочей книги с размером меньше 10 МБ **<sup>3</sup>**|Да **<sup>3</sup>**|  
  
 **<sup>1</sup>**[Microsoft Power BI](http://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).  
  
 **<sup>2</sup>**  [Рабочие книги PowerPivot как источник данных](http://blogs.technet.com/b/excel_services__powerpivot_for_sharepoint_support_blog/archive/2013/02/15/powerpivot-workbook-as-a-data-source.aspx)  
  
 **<sup>3</sup>**[поддержка мобильных устройств через средства бизнес-аналитики (BI)](https://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) и [планирование служб Reporting Services и поддержки Power View в браузере (Reporting Services 2014)](https://msdn.microsoft.com/library/ms156511.aspx).  
  
## <a name="more-information"></a>Дополнительные сведения  
  
-   [Возможности бизнес-аналитики в Excel, SharePoint Online и Power BI для Office 365](https://technet.microsoft.com/en-us/library/dn198235.aspx).  
  
-   Сведения о требованиях для использования синонимов см. в разделе [Добавление синонимов в модель данных Power Pivot Excel](https://support.office.com/Article/Add-synonyms-to-a-Power-Pivot-Excel-data-model-345f4f5b-5ec2-4998-bc46-a26bdc0810b6?ui=en-US&rs=en-US&ad=US).  
  
-   [Office Online. Выбор социальной сети предприятия: Yammer или канал новостей? ](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
-   [Power BI для Office 365](https://www.microsoft.com/powerbi/default.aspx).  
  
-   [Цены на Power BI](https://www.microsoft.com/powerBI/pricing.aspx).  
  
-   [Сравнение сайт центра бизнес-аналитики с Power BI для Office 365 сайтов](https://technet.microsoft.com/library/dn394343\(v=office.15\).aspx).  
  
-   [Общие сведения о Microsoft BI Reporting и средства анализа](https://go.microsoft.com/fwlink/p/?LinkId=617093)  
  
## <a name="community-content"></a>Содержимое сообщества  
 [Сравнение локальных и облачных средств бизнес-аналитики Майкрософт](http://businessintelligist.com/2014/02/07/microsoft-self-service-bi-on-premise-vs-could/).  
  
  
