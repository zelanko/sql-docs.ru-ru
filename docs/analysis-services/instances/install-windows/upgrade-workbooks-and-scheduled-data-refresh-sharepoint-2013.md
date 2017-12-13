---
title: "Обновление книг и запланированное обновление данных (SharePoint 2013) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a49c4af4-e243-4926-be97-74da1f9d54eb
caps.latest.revision: "20"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3d1ecdb0be095931b952b3ef93ee566db40dfb5f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013"></a>Обновление книг и запланированное обновление данных (SharePoint 2013)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]В этом разделе описываются способы использования книг, созданных в предыдущих [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] средами и обновление [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] книги, чтобы воспользоваться преимуществами новых возможностей, представленных в этом выпуске. Дополнительные сведения о новых возможностях см. в статье [Новые возможности PowerPivot](http://go.microsoft.com/fwlink/?LinkID=203917).  
  
> [!WARNING]  
>  Невозможно выполнить откат обновления для книг, автоматически обновленных на сервере. После обновления книги она остается обновленной. Для использования предыдущей версии можно повторно опубликовать предыдущую книгу в SharePoint, восстановить предыдущую версию или повторно использовать книгу. Дополнительные сведения о восстановлении и повторном использовании документа в SharePoint см. в разделе [Планирование защиты содержимого с использованием корзин и управления версиями](http://go.microsoft.com/fwlink/?LinkId=238669).  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Общие сведения об обновлении книг](#bkmk_overview)  
  
-   [Выполните обновление до книг версии SQL Server 2012 с пакетом обновления 1 (SP1) от книг 2008 R2](#bkmk_to_2012sp1_from_2008r2)  
  
-   [Обновление до книг Office 2013 из версий, созданных с помощью надстройки PowerPivot 2012 для Excel](#bkmk_to_2012sp1_from_2012)  
  
-   [Обновление до книг SQL Server 2012 из версий, созданных с помощью надстройки 2008 R2 PowerPivot для Excel 2010](#bkmk_to_2012_from_2008R2)  
  
-   [Запуск нескольких версий книги на сервере более новых версий](#bkmk_runold)  
  
##  <a name="bkmk_overview"></a> Общие сведения об обновлении книг  
 Книга [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] — это книга Excel, которая содержит внедренные данные [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Обновление книги обеспечивает два преимущества.  
  
-   Используйте новые возможности [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)].  
  
-   Становится возможным плановое обновление данных для книг, которые работают с сервером служб [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] Analysis Services в режиме интеграции с SharePoint.  
  
> [!IMPORTANT]  
>  Нельзя выполнить откат обновленной книги, поэтому обязательно создайте копию файла, если предполагается его использование в предыдущих версиях [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)]или [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].  
  
 В следующей таблице содержатся сведения о наличии поддержки и поведении книг [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в зависимости от среды, в которой была создана книга. Описанное поведение включает общие методы работы пользователя, поддерживаемые варианты обновления книги в определенной среде и плановое обновление данных книги, которая еще не была обновлена.  
  
### <a name="workbook-behavior-and-upgrade-options"></a>Поведение и варианты обновления книги  
  
|Создано в|\<|Поддержка и поведение|>|  
|----------------|--------|--------------------------|--------|  
||**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2008 R2 для SharePoint 2010**|**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2012 для SharePoint 2010**|**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2012 с пакетом обновления 1 (SP1) для SharePoint 2013**|  
|**2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel 2010**|Все компоненты|**Взаимодействие.** Пользователи могут взаимодействовать с книгой в браузере и использовать ее в качестве источника данных для других решений.<br /><br /> **Обновление.** Книги в библиотеке документов будут автоматически обновлены, если для системной службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме SharePoint включено автоматическое обновление.<br /><br /> **Расписание обновления данных.** НЕ поддерживается. Книгу необходимо обновить.|**Взаимодействие.** Пользователи могут взаимодействовать с книгой и использовать ее в качестве источника данных для других решений.<br /><br /> **Обновление.** Автоматическое обновление недоступно. Необходимо вручную обновить книги 2008 R2 до версии 2012 или до версии Office 2013.<br /><br /> **Расписание обновления данных.** НЕ поддерживается. Книгу необходимо обновить.|  
|**[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] 2012 для Excel**|Не поддерживается|Все компоненты|**Взаимодействие.** Пользователи могут взаимодействовать с книгой в браузере и использовать ее в качестве источника данных для других решений. Расписание обновления данных доступно.<br /><br /> **Обновление.** Автоматическое обновление не поддерживается. Пользователи могут вручную обновить книги до версии Office 2013.<br /><br /> **Расписание обновления данных:** поддерживается.|  
|**Excel 2013**|Не поддерживается|Не поддерживается|Все компоненты|  
  
##  <a name="bkmk_to_2012sp1_from_2008r2"></a> Выполните обновление до книг версии SQL Server 2012 с пакетом обновления 1 (SP1) от книг 2008 R2  
 В этом разделе описывается обновление SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] с пакетом обновления 1 (SP1) для книг Excel 2013 из SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для книг Excel 2010.  
  
 **Изменения в работе.** Книги SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] не обновляются автоматически, если они используются в SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] с пакетом обновления 1 (SP1) для SharePoint 2013. Поэтому плановые обновления данных не будут распространятся на книги SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
 Книги 2008 R2 открываются в [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013, но плановые обновления данных не выполняются. При просмотре журнала обновления обнаруживается сообщение об ошибке следующего вида:  
  
 Книга содержит неподдерживаемую модель [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Модель [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в книге представлена в формате SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel 2010. Поддерживаются следующие модели [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] :  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel 2010  
  
-   SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel 2013  
  
 **Обновление книги.** Плановое обновление данных не будет работать, пока книга не будет обновлена до книги 2012. Для обновления книги и содержащейся в ней модели выполните одно из следующих действий.  
  
-   Скачайте и откройте книгу в Microsoft Excel 2010 с помощью установленной надстройки SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel.  
  
     Откройте окно [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и обновите модель [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
     Сохраните книгу и повторно опубликуйте ее в SharePoint.  
  
-   Загрузите и откройте книгу в Microsoft Excel 2013.  
  
     Откройте окно [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и обновите модель [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
     Затем сохраните книгу и повторно опубликуйте ее на сервере SharePoint.  
  
 Дополнительные сведения об изменениях функций служб Analysis Services см. в разделе [Изменение действия функций служб Analysis Services в SQL Server 2016](../../../analysis-services/behavior-changes-to-analysis-services-features-in-sql-server-2016.md).  
  
 Дополнительные сведения о журнале обновления см. в разделе [Просмотр журнала обновления данных (Power Pivot для SharePoint)](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md).  
  
##  <a name="bkmk_to_2012sp1_from_2012"></a> Обновление до книг Office 2013 из версий, созданных с помощью надстройки PowerPivot 2012 для Excel  
 В этом разделе описывается обновление **до** SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] с пакетом обновления 1 (SP1) в Excel 2013 **из** SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для книг Excel 2010.  
  
 Обновление книги устраняет следующие ошибки, которые возникают при попытке обновления данных книги предшествующей версии по расписанию:  
  
 "Обновление книг, созданных в предыдущей версии [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , недоступно".  
  
 **Обновление книги**  
  
1.  Обновите каждую книгу вручную, открыв ее в Microsoft Excel 2013.  
  
2.  Для обновления книги и содержащейся в ней модели загрузите и откройте книгу в приложении Microsoft Excel 2013.  
  
3.  Откройте окно [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] и обновите модель [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] .  
  
4.  Затем сохраните книгу и повторно опубликуйте ее на сервере SharePoint 2013.  
  
##  <a name="bkmk_to_2012_from_2008R2"></a> Обновление до книг SQL Server 2012 из версий, созданных с помощью надстройки 2008 R2 PowerPivot для Excel 2010  
 В этом разделе описывается обновление **до** SQL Server 2012 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в Excel 2010 **из** SQL Server 2008 R2 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для книг Excel 2010.  
  
 Обновление книги устраняет следующие ошибки, которые возникают при попытке обновления данных книги предшествующей версии по расписанию:  
  
 "Обновление книг, созданных в предыдущей версии [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , недоступно".  
  
 **Обновление книги**  
  
 Существует два способа обновления.  
  
1.  Обновление каждой книги вручную путем ее открытия в Excel на компьютере с установленной версией [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel с последующей повторной публикацией на сервере. При открытии книги в последней версии надстройки выполняются следующие внутренние операции. Поставщик данных в строке подключения к данным книги обновляется до MSOLAP.5, обновляются также метаданные, и выполняется воссоздание связей для соответствия более новой реализации.  
  
2.  Или же администратор SharePoint может включить функцию автоматического обновления для службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в ферме SharePoint, чтобы автоматически обновить книгу [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)][!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] при обновлении данных по расписанию (обновляются только книги, для которых настроено обновление данных по расписанию).  
  
    > [!NOTE]  
    >  Автоматическое обновление — это функция настройки сервера; его нельзя включить или отключить для конкретной книги, библиотеки или семейства веб-сайтов.  
  
 **Настройка автоматического обновления во время обновления данных**  
  
 Чтобы включить автоматическое обновление, необходимо установить флажок **Автоматически обновлять книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для обновления данных с сервера** в средстве настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]. Флажок находится на странице **Обновление системной службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]** этого средства, а также на странице **Создание приложения службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]** при настройке новой установки.  
  
 Запустив следующий командлет, можно проверить, включена ли функция автоматического обновления.  
  
```  
PS C:\Windows\system32> Get-PowerPivotSystemService  
```  
  
 Результатом вызова Get-PowerPivotSystemService будет список свойств вместе с соответствующими значениями. В списке свойств нужно найти **WorkbookUpgradeOnDataRefresh** . Оно будет иметь значение **true** , если автоматическое обновление включено. Если же это свойство имеет значение **false**, перейдите на следующий шаг и включите автоматическое обновление книги.  
  
 Чтобы включить автоматическое обновление книги, выполните следующую команду:  
  
```  
PS C:\Windows\system32> Set-PowerPivotSystemService –WorkbookUpgradeOnDataRefresh:$true –Confirm:$false  
```  
  
 Обновив книгу, вы можете обновлять данные по расписанию, а также использовать новые возможности надстройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для Excel.  
  
##  <a name="bkmk_runold"></a> Запуск нескольких версий книги на сервере более новых версий  
 Книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] старых и новых версий можно использовать параллельно на экземпляре [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)].  
  
 В зависимости от метода установки сервера **может потребоваться** установить предыдущую версию поставщика OLE DB служб Analysis Services, чтобы на одном сервере можно было открывать книги как старых, так и новых версий.  
  
 Обратите внимание, что не поддерживается публикация книг новой версии на предшествующих экземплярах SQL Server [!INCLUDE[ssGeminiShort](../../../includes/ssgeminishort-md.md)] . Экземпляр [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] не загружает книги, созданные в версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)], а экземпляр SQL Server 2012 не загружает книги Office 2013 с расширенными моделями данных, созданные с помощью версии [!INCLUDE[ssSQL11SP1](../../../includes/sssql11sp1-md.md)] [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] в Excel.  
  
###  <a name="bkmk_msolapxslx"></a> Как проверить сведения о поставщике данных MSOLAP в книге PowerPivot  
 Чтобы определить текущую версию поставщика OLE DB для книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , выполните следующие действия. Для проверки сведений подключения к данным не требуется установка надстройки [!INCLUDE[ssGeminiClient](../../../includes/ssgeminiclient-md.md)] .  
  
1.  Нажмите кнопку **Соединения**на вкладке «Данные» в Excel. Нажмите кнопку **Свойства**.  
  
2.  На вкладке **Определение** в начале строки подключения отображается версия поставщика.  
  
     **Provider=MSOLAP.5** указывает, что книга версии [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
     **Provider=MSOLAP.4** указывает на версию [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)].  
  
     **Data Source=$Embedded$** указывает, что это книга [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] использует внедренную базу данных.  
  
###  <a name="bkmk_msolappc"></a> Проверка текущей версии поставщика данных MSOLAP на локальном компьютере  
 Чтобы определить текущую версию поставщика OLE DB на сервере или рабочей станции, на которых запускаются книги [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , используйте инструкции, приведенные ниже. Сведения о текущей версии позволят выполнять диагностику ошибок подключений к данным после обновления.  
  
1.  В редакторе реестра перейдите в раздел HKEY_CLASSES_ROOT  
  
2.  С помощью прокрутки перейдите в раздел MSOLAP. Убедитесь, что в списке поставщиков OLAP, установленных в системе, указан MSOLAP.5. Убедитесь, что для параметра MSOLAP | CurVer задано значение MSOLAP.5  
  
## <a name="see-also"></a>См. также:  
 [Перенос Power Pivot в SharePoint 2013](../../../analysis-services/instances/install-windows/migrate-power-pivot-to-sharepoint-2013.md)   
 [Обновление Power Pivot для SharePoint](../../../database-engine/install-windows/upgrade-power-pivot-for-sharepoint.md)   
 [Новые возможности в службах Analysis Services](../../../analysis-services/what-s-new-in-analysis-services.md)   
 [Обновление представления данных, журнал &#40; Power Pivot для SharePoint &#41;](../../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
  
