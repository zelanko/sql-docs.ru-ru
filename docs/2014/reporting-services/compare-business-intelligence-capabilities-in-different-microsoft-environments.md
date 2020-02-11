---
title: Сравнение возможностей бизнес-аналитики в разных средах Майкрософт | Документация Майкрософт
ms.prod: sql-server-2014
ms.technology: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.custom: ''
ms.date: 12/15/2019
ms.openlocfilehash: a5f9e9b52186a2d4569ac30a591ae95acfa36101
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75656591"
---
# <a name="compare-business-intelligence-capabilities-in-different-microsoft-environments"></a>Сравнение возможностей бизнес-аналитики в разных средах Microsoft

Средства бизнес-аналитики Майкрософт [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] могут развертываться в нескольких различных средах, в том числе [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с SharePoint Server, SharePoint Online и Power BI для Office 365. В этом разделе приводится сравнение компонентов и функций, поддерживаемых в каждой среде.  
  
Дополнительные сведения о сравнении SharePoint Server и SharePoint Online см. в разделе [Сравнение планов и параметров SharePoint](https://products.office.com/SharePoint/compare-sharepoint-plans).  
  
## <a name="author-and-manage-bi-reports-and-dashboards"></a>Создание и управление отчетами бизнес-аналитики и панелями мониторинга  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online план 2|Power BI для Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Узлы бизнес-аналитики|[!INCLUDE[ssGemini](../includes/ssgemini-md.md)]Галерея|нет|Сайт Power BI|  
|Центральное управление данными, совместное использование запросов и управление ими|нет|нет|Да ** <sup>1</sup>**|  
|Интеграция с Master Data Services (MDS) и Data Quality Services (DQS)|Да|нет|нет|  
|Расписание обновления данных|Да, но не поддерживает рабочие книги, содержащие данные Power Query|нет|Да|  
|Запрос на естественном языке (Q&A)|нет|нет|Да ** <sup>2</sup>**|  
|Предсказуемое прогнозирование|нет|нет|Да ** <sup>3</sup>**|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]Интеграция|Да|нет|нет|  
|
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]Интеграция (многомерные и табличные данные)|Да|нет|нет|  
|Экспорт интерактивных панелей мониторинга Power View в презентацию PowerPoint|Да|нет|нет|  
|Создание панели мониторинга в браузере|Да|нет|нет|  
|Отслеживание использования|Да|нет|Да|  
|Использование безопасности на основе строк кубов [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|Да|нет|нет|  
|||||

 **<sup>1</sup>**  [понимание роли администраторы данных в управление данными](https://support.office.com/Article/Understanding-the-Role-of-Data-Stewards-in-Data-Management-ae3352f3-4389-45e8-a682-7fd6edb92524?ui=en-US&rs=en-US&ad=US) и [видео: Управление Power BI информацией и администраторе данных](https://www.youtube.com/watch?v=8dHOj68ts7c).  
  
 **<sup>2</sup>**  [Power BI Q&а. Оптимизация Power BI книги (облачное моделирование)](https://powerbi.microsoft.com/nl-nl/blog/new-in-power-bi-cloud-modeling-for-q-and-a/).  
  
 **<sup>3</sup>**  [Знакомство с новыми возможностями прогнозирования в Power View для Office 365](https://blogs.msdn.com/b/powerbi/archive/2014/05/08/introducing-new-forecasting-capabilities-in-power-view-for-office-365.aspx).  
  
## <a name="view-and-browse-bi-data-reports-and-dashboards"></a>Просмотр и обзор данных, отчетов и панелей мониторинга бизнес-аналитики  
  
||SQL Server 2014 & SharePoint Server 2013|SharePoint Online план 2|Power BI для Office 365|  
|-|----------------------------------------------|------------------------------|-----------------------------|  
|Просмотр рабочих книг Microsoft Excel в браузере|Да, если размер рабочей книги меньше, чем 2 ГБ|Да, если размер рабочей книги меньше, чем 10 ГБ|Да, если размер рабочей книги меньше, чем 250 МБ|  
|Просмотр данных в браузере в HTML5|нет|нет|Да|  
|Приложения бизнес-аналитики для удаленного доступа к отчетам и панелям мониторинга|нет|нет|Да ** <sup>1</sup>**|  
|Книга Excel с [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] в качестве источника данных **<sup>2</sup>**|Да|нет|нет|  
|Возможность использования функций в различных браузерах и версиях|Да, для визуализации не в Power View **<sup>3</sup>**|Да, для файлов рабочей книги с размером меньше 10 МБ **<sup>3</sup>**|Да ** <sup>3</sup>**|  
|||||

 **<sup>1</sup>**  [Power BI Майкрософт](https://apps.microsoft.com/windows/app/microsoft-power-bi/b7e7c94d-2ea3-4fa6-a277-9d19a1f697ba).  
  
 **<sup>2</sup>**  [книги PowerPivot в качестве источника данных](https://support.office.com/article/Power-Pivot-Powerful-data-analysis-and-data-modeling-in-Excel-A9C2C6E2-CC49-4976-A7D7-40896795D045)  
  
 **<sup>3</sup>**  [Поддержка мобильных устройств в средствах бизнес-аналитики (BI)](https://msdn.microsoft.com/library/dn151146\(v=sql.110\).aspx) и [Планирование поддержки Reporting Services и Power View браузера (Reporting Services 2014)](https://msdn.microsoft.com/library/ms156511.aspx).  
  
## <a name="more-information"></a>Дополнительные сведения  
  
- [Возможности бизнес-аналитики в Excel и Office 365](https://support.office.com/article/BI-capabilities-in-Excel-and-Office-365-26c0548e-124c-4fd3-aab3-5f64568cb743).  
  
- Сведения о требованиях к использованию синонимов см. в статье [оптимизация Power BI Q&A с синонимами &](https://blog.pragmaticworks.com/optimizing-power-bi-qa-with-synonyms-phrasing-using-cloud-modeling) выражения по адресу pragmaticworks.com.  
  
- [Office Online, выберите корпоративную социальную сеть: Yammer или канал новостей?](https://support.office.com/article/Pick-your-enterprise-social-network-Yammer-or-Newsfeed-21954c85-4384-47d4-96c2-dfa1c9d56e66?ui=en-US&rs=en-US&ad=US).  
  
- [Power BI для Office 365](https://www.microsoft.com/powerbi/default.aspx).  
  
- [Power BI цены](https://www.microsoft.com/powerBI/pricing.aspx).  
  
- [Средства Microsoft Business Intelligence (BI) для анализа и отчетности](../reporting-services/choosing-microsoft-business-intelligence-bi-tools-for-analysis-and-reporting.md)  
  
## <a name="community-content"></a>Материалы сообщества

