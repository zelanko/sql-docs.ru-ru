---
title: "Заметки о выпуске SQL Server 2012 с пакетом обновления 1 (SP1) | Документация Майкрософт"
ms.prod: sql-server-2012
ms.technology: server-general
ms.custom: 
ms.date: 01/31/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72171357-28de-4edd-bdfd-194f97225a6f
caps.latest.revision: 49
author: byham
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 47cba5e99626a7b378c29a9dde4923963fae09da
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-2012-sp1-release-notes"></a>SQL Server 2012 SP1 Release Notes
В этих заметках о выпуске содержится описание известных проблем. Их необходимо прочитать перед установкой или устранением проблем в [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssSQL11](../includes/sssql11-md.md)] с пакетом обновления 1 (SP1). Этот документ «Заметки о выпуске» доступен только для загрузки в сети и постоянно обновляется. Этот документ не содержится на установочном носителе.  
  
## <a name="bkmk_top"></a>Содержание  
[1.0 Перед началом установки](#bmk_Install)  
  
[2.0 Службы Analysis Services и PowerPivot](#bkmk_AS)  
  
[3.0 Службы Reporting Services](#bkmk_RS)  
  
[4.0 Службы Data Quality Services](#bkmk_DQS)  
  
[5.0 Экспресс-выпуск SQL Server](#bkmk_Express)  
  
[6.0 Служба системы отслеживания измененных данных и конструктор для Oracle компании Attunity](#bkmk_CDC)  
  
[7.0 Платформа приложения уровня данных SQL Server (DACFx)](#DACFx)  
  
[8.0 Известные проблемы, исправленные в этом пакете обновления](#bkmk_known_issues_fixed)  
  
## <a name="bmk_Install"></a>1.0 Перед началом установки  
Прежде чем приступать к установке SQL Server 2012 с пакетом обновления 1 (SP1), необходимо учесть следующее.  
  
### <a name="11-reinstalling-an-instance-of-sql-server-failover-custer-fails-if-you-use-the-same-ip-address"></a>1.1. Переустановка экземпляра отказоустойчивого кластера SQL Server завершается ошибкой, если используется один и тот же IP-адрес  
**Проблема.** Если указан неправильный IP-адрес в ходе установки экземпляра отказоустойчивого кластера SQL Server, установка завершится с ошибкой. После удаления сбойного экземпляра при попытке повторной установки экземпляра отказоустойчивого кластера SQL Server с тем же именем экземпляра и правильным IP-адресом установка также завершается сбоем. Сбой возникает в связи с повторяющейся группой ресурсов, которая остается после предыдущей попытки установки.  
  
**Решение.** Чтобы устранить эту проблему, используйте другое имя экземпляра во время переустановки или вручную удалите группу ресурсов перед переустановкой. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server](http://msdn.microsoft.com/library/ms191545).  
  
### <a name="12-choose-the-correct-file-to-download-and-install"></a>1.2. Выбор требуемого файла для загрузки и установки  
Используйте следующую таблицу, чтобы определить, какой файл необходимо загрузить и установить. Перед установкой пакета обновления убедитесь, что соблюдены все требования к системе. Требования к системе приведены на страницах загрузки, ссылки на которые указаны в таблице.  
  
|Если текущей установленной версией является...|И необходимо выполнить следующее...|Загрузите и установите...|  
|-------------------------------------------|----------------------|---------------------------|  
|**32-разрядные установки:**|||  
|32-разрядная версия любого выпуска SQL Server 2012|Обновление до 32-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|32-разрядная версия SQL Server 2012 RTM Express|Обновление до 32-разрядной версии SQL Server 2012 Express с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|32-разрядная версия только клиента и средств управления для SQL Server 2012 (включая SQL Server 2012 Management Studio)|Обновление клиента и средств управления до 32-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLManagementStudio_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|32-разрядная версия SQL Server 2012 Management Studio Express|Обновление до 32-разрядной версии SQL Server 2012 Management Studio Express с пакетом обновления 1 (SP1)|SQLManagementStudio_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|32-разрядная версия любого выпуска SQL Server 2012 **и** 32-разрядная версия клиента и средств управляемости (включая SQL Server 2012 RTM Management Studio)|Обновление всех продуктов до 32-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x86-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|32-разрядная версия одного или нескольких средств из [пакета дополнительных компонентов Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/details.aspx?id=16978)|Обновление средств до 32-разрядной версии пакета дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)|Один или несколько файлов из [пакета дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Отсутствует 32-разрядная установка SQL Server 2012|Установите 32-разрядную версию SQL Server 2012 с пакетом обновления 1 (SP1): новый экземпляр с предустановленным пакетом обновления 1 (SP1)|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **и** SQLServer2012SP1-FullSlipstream-x86-ENU.box [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Отсутствует 32-разрядная установка SQL Server 2012 Management Studio|Установите 32-разрядную версию SQL Server 2012 Management Studio, включая пакет обновления 1 (SP1)|SQLManagementStudio_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|Отсутствует 32-разрядная версия SQL Server 2012 RTM Express|Установите 32-разрядную версию SQL Server 2012 Express, включая пакет обновления 1 (SP1)|SQLEXPR32_x86_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkId=267905)|  
|32-разрядная установка **SQL Server 2008** или **SQL Server 2008 R2**|**Обновление на месте** до 32-разрядной версии SQL Server 2012, включая пакет обновления 1 (SP1)|SQLServer2012SP1-FullSlipstream-x86-ENU.exe **и** SQLServer2012SP1-FullSlipstream-x86-ENU.box [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|**64-разрядные установки:**|||  
|64-разрядная версия любого выпуска SQL Server 2012|Обновление до 64-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|64-разрядная версия SQL Server 2012 RTM Express|Обновление до 64-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|64-разрядная версия только клиента и средств управляемости для SQL Server 2012 (включая SQL Server 2012 Management Studio)|Обновление клиента и средств управляемости до 64-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLManagementStudio_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|64-разрядная версия SQL Server 2012 Management Studio Express|Обновление до 64-разрядной версии SQL Server 2012 Management Studio Express с пакетом обновления 1 (SP1)|SQLManagementStudio_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|64-разрядная версия любого выпуска SQL Server 2012 **и** 64-разрядная версия клиента и средств управляемости (включая SQL Server 2012 RTM Management Studio)|Обновление всех продуктов до 64-разрядной версии SQL Server 2012 с пакетом обновления 1 (SP1)|SQLServer2012SP1-KB2674319-x64-ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|64-разрядная версия одного или нескольких средств из [пакета дополнительных компонентов Microsoft SQL Server 2012 RTM](http://www.microsoft.com/download/en/details.aspx?id=16978)|Обновление средств до 64-разрядной версии пакета дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)|Один или несколько файлов из [пакета дополнительных компонентов Microsoft SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266)|  
|Отсутствует 64-разрядная установка SQL Server 2012|Установить 64-разрядную версию SQL Server 2012 с пакетом обновления 1 (SP1): новый экземпляр с предустановленным пакетом обновления 1 (SP1)|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **и** SQLServer2012SP1-FullSlipstream-x64-ENU.box [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
|Отсутствует 64-разрядная установка SQL Server 2012 Management Studio|Установить 64-разрядную версию SQL Server 2012 Management Studio, включая пакет обновления 1 (SP1)|SQLManagementStudio_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|Отсутствует 64-разрядная версия SQL Server 2012 RTM Express|Установить 64-разрядную версию SQL Server 2012 Express, включая пакет обновления 1 (SP1)|SQLEXPR_x64_ENU.exe [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=267905)|  
|64-разрядная установка **SQL Server 2008** или **SQL Server 2008 R2**|**Обновление на месте** до 64-разрядной версии SQL Server 2012, включая пакет обновления 1 (SP1)|SQLServer2012SP1-FullSlipstream-x64-ENU.exe **и** SQLServer2012SP1-FullSlipstream-x64-ENU.box [по этой ссылке](http://go.microsoft.com/fwlink/p/?LinkID=268158)|  
  
![Значок стрелки, используемый для ссылки возврата в начало](../release-notes/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[Содержимое](#bkmk_top)  
  
## <a name="bkmk_AS"></a>2.0 Службы Analysis Services и PowerPivot  
  
### <a name="21-powerpivot-configuration-tool-does-not-create-the-powerpivot-gallery"></a>2.1. Средство настройки PowerPivot не создает коллекцию PowerPivot  
**Проблема.** Средство настройки PowerPivot подготавливает сайт группы, поэтому не создается коллекция PowerPivot.  
  
**Решение.** Создайте новое приложение (библиотеку).  
  
1.  Убедитесь в том, что активна **Функция интеграции с PowerPivot для семейств веб-сайтов** .  
  
2.  На странице **Содержание сайта** существующего сайта выберите пункт **Добавить приложение**.  
  
3.  Щелкните **Коллекция PowerPivot**.  
  
### <a name="22-to-use-powerpivot-for-excel-with-excel-2013-you-must-use-the-add-in-that-is-installed-with-excel"></a>2.2. Для использования PowerPivot для Excel с Excel 2013 необходимо использовать надстройку, установленную с Excel  
**Проблема.** Начиная с Office 2010, PowerPivot для Excel представляет собой отдельную надстройку, которую можно скачать по адресу [http://www.microsoft.com/bi/powerpivot.aspx](http://www.microsoft.com/bi/powerpivot.aspx). Ее можно также загрузить из [центра загрузки Майкрософт](http://www.microsoft.com/download/details.aspx?id=29074). Обратите внимание, что для скачивания доступны две версии надстройки PowerPivot. Одна из них поставляется с SQL Server 2008 R2, а вторая — с SQL Server 2012. Но для Оffice 2013 PowerPivot для Excel поставляется с Оffice и устанавливается при установке Excel. Версии PowerPivot для Excel 2010 в SQL Server 2008 R2 и SQL Server 2012 несовместимы с Excel 2013, но все равно можно установить PowerPivot для Excel 2010 на клиентском компьютере, если есть необходимость эксплуатировать Excel 2010 параллельно с Excel 2013. Другими словами, могут сосуществовать&2; версии Excel, а вместе с ними соответствующие надстройки PowerPivot.  
  
**Решение.** Чтобы использовать PowerPivot для Excel 2013, необходимо включить надстройку COM. В Excel 2013 выберите **Файл** | **Параметры** | **Надстройки**. В раскрывающемся списке выберите **Управление** , а затем щелкните **Надстройки COM** и нажмите кнопку **Перейти**. В окне **Надстройки COM**выберите **Microsoft Office PowerPivot для Microsoft Excel 2013** и нажмите кнопку **ОК**.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../release-notes/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[Содержимое](#bkmk_top)  
  
## <a name="bkmk_RS"></a>3.0 Службы Reporting Services  
  
### <a name="31-install-and-configure-sharepoint-server-2013-prior-to-installing-reporting-services"></a>3.1. Установка и настройка SharePoint Server 2013 перед установкой служб Reporting Services  
**Проблема.** Выполнение следующих требований **перед** установкой служб SQL Server Reporting Services (SSRS).  
  
1.  Запустите инструмент подготовки продуктов SharePoint 2013.  
  
2.  Установите Install SharePoint Server 2013.  
  
3.  Запустите мастер настройки продуктов SharePoint 2013 или выполните аналогичный набор действий по конфигурации для настройки фермы SharePoint.  
  
**Решение.**  При установке [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint до настройки фермы SharePoint действия, которые потребуется выполнить, чтобы обойти проблему, зависят от того, какие еще компоненты установлены.  
  
### <a name="32-power-view-in-sharepoint-server-2013-requires-microsoftanalysisservicesspclientdll"></a>3.2. Для Power View в SharePoint Server 2013 требуется библиотека Microsoft.AnalysisServices.SPClient.dll  
**Проблема.** [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] не устанавливает требуемый компонент, библиотеку **Microsoft.AnalysisServices.SPClient.dll**. При установке предварительной версии SharePoint Server 2013 Preview и [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в режиме интеграции с SharePoint, если пакет установщика PowerPivot для SharePoint 2013, файл **spPowerPivot.msi**, не скачан и не запущен, Power View не будет работать. Нарушения будут проявляться следующим образом.  
  
**Симптомы.** При попытке создания отчета Power View отображается сообщение об ошибке подобное следующему:  
  
-   «Не удалось установить соединение с источником данных...»  
  
Во внутренних сведениях об ошибке будет содержаться примерно такое сообщение:  
  
-   «Значение "SharePoint Principal" не поддерживается для свойства строки подключения "User Identity"».  
  
**Решение.** Установите пакет установщика PowerPivot для SharePoint 2013 (**spPowerPivot.msi**) на сервере SharePoint Server 2013. Пакет установщика доступен в составе пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../includes/sssql11sp1-md.md)] . Пакет дополнительных компонентов можно загрузить из центра загрузки [!INCLUDE[msCoName](../includes/msconame-md.md)] по ссылке [Пакет дополнительных компонентов SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266)  
  
### <a name="33-power-view-sheets-in-a-powerpivot-workbook-are-deleted-after-a-scheduled-data-refresh"></a>3.3. После планового обновления данных листы Power View в книге PowerPivot удаляются  
**Проблема.**В надстройке PowerPivot для SharePoint при использовании **планового обновления данных** для книги с Power View удаляются все листы Power View.  
  
**Решение.**Чтобы использовать **Scheduled Data Refresh** с книгами Power View, создайте книгу PowerPivot, представляющую собой просто модель данных. Создайте отдельную книгу с листами Excel и листами Power View, ссылающимися на книгу PowerPivot с моделью данных. Обновление данных можно планировать только для книги PowerPivot с моделью данных.  
  
## <a name="bkmk_DQS"></a>4.0 Службы Data Quality Services  
  
### <a name="41-dqs-available-in-the-incorrect-edition-of-sql-server-2012"></a>4.1. Доступ к DQS в неверном выпуске SQL Server 2012  
**Проблема.** В версии RTM [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] компонент служб Data Quality Services (DQS) поддерживается в выпусках SQL Server, отличных от Enterprise, Business Intelligence и Developer. После установки SQL Server 2012 с пакетом обновления 1 (SP1) службы DQS будут недоступны во всех выпусках, за исключением Enterprise, Business Intelligence и Developer.  
  
**Решение.**Если службы DQS используются в неподдерживаемом выпуске, проведите обновление до поддерживаемого выпуска или удалите зависимость от этой функции из приложений.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../release-notes/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[Содержимое](#bkmk_top)  
  
## <a name="bkmk_Express"></a>5.0 Экспресс-выпуск SQL Server  
  
### <a name="51-full-version-of-sql-server-management-studio-available-in-sql-server-2012-express-sp1"></a>5.1. Полная версия SQL Server Management Studio доступна в SQL Server 2012 Express с пакетом обновления 1 (SP1)  
Выпуск SQL Server 2012 Express с пакетом обновления 1 (SP1) включает полную версию SQL Server 2012 Management Studio (которая ранее предоставлялась только на DVD-диске SQL Server 2012) вместо SQL Server 2012 Management Studio Express. Чтобы загрузить и установить SQL Server 2012 Express с пакетом обновления 1 (SP1), см. раздел [SQL Server 2012 Express с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?linkid=267905).  
  
![Значок стрелки, используемый для ссылки возврата в начало](../release-notes/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[Содержимое](#bkmk_top)  
  
## <a name="bkmk_CDC"></a>6.0 Служба системы отслеживания измененных данных и конструктор для Oracle компании Attunity  
  
### <a name="61-upgrading-the-cdc-service-and-designer"></a>6.1. Обновление службы CDC и конструктор  
**Проблема.** Если конструктор системы отслеживания измененных данных (Change Data Capture Designer) для Oracle и служба системы отслеживания измененных данных (Change Data Capture Service) для Oracle от Attunity установлены на компьютере одновременно с установкой SQL Server 2012 с пакетом обновления 1 (SP1), эти компоненты не обновляются при установке пакета обновления 1 (SP1).  
  
**Решение.** Обновление компонентов CDC до последней версии:  
  
1.  Загрузите файлы MSI, относящиеся к службе системы отслеживания измененных данных для Oracle от Attunity, на [странице загрузки пакета дополнительных компонентов для SQL Server 2012 с пакетом обновления 1 (SP1)](http://go.microsoft.com/fwlink/p/?LinkID=268266).  
  
2.  Запустите файл MSI.  
  
![Значок стрелки, используемый для ссылки возврата в начало](../release-notes/media/uparrow16x16.gif "Значок стрелки, используемый для ссылки возврата в начало")[Содержимое](#bkmk_top)  
  
## <a name="DACFx"></a>7.0 Платформа приложения уровня данных SQL Server (DACFx)  
**Поддержка обновления на месте**  
  
Эта версия платформы приложения уровня данных (DACFx) поддерживает обновление на месте от предыдущей версии, поэтому нет необходимости удалять предыдущую установку DACFx перед обновлением до этого выпуска. Вы можете найти будущие выпуски DACFx [здесь](https://msdn.microsoft.com/library/dn702988.aspx).  
  
**Поддержка селективного XML-индекса**  
  
SQL Server 2012 с пакетом обновления 1 (SP1) включает поддержку [селективного XML-индекса (SXI)](http://msdn.microsoft.com/en-us/598ecdcd-084b-4032-81b2-eed6ae9f5d44), новой возможности SQL Server, предоставляющей новый способ индексирования данных в XML-столбцах с повышенными производительностью и эффективностью.  
  
DACFx теперь поддерживает SXI-индексы во всех сценариях и клиентских средствах приложения уровня данных. SXI поддерживается только в последней версии SSDT. Версия SSDT RTM и версия от сентября 2012 г. не поддерживают SXI.  
  
**Поддержка собственного формата данных с форматированием BCP**  
  
Раньше для хранения табличных данных в пакетах DACPAC и BACPAC использовался формат данных JSON. После этого обновления форматом хранения данных является Native BCP. Это изменение повышает правильность типов данных SQL Server для DACFx, включая поддержку типов SQL_Variant types и повышенную производительность развертывания данных для крупных баз данных.  
  
**Сохранение состояния проверочного ограничения при создании или развертывании пакетов**  
  
Ранее DACFx не сохраняла состояние (WITH CHECK/NOCHECK) проверочных ограничений, определенных для таблиц в схеме базы данных, и не сохраняла эту информацию в пакетах DACPAC. Это поведение могло в потенциале привести к проблемам при развертывании пакета из-за существования табличных данных, нарушающих проверочные ограничения. После этого обновления DACFx сохраняет текущее состояние проверочных ограничений в DACPAC при извлечении из базы данных и, соответственно, восстанавливает это состояние при развертывании пакета.  
  
**Обновления в SqlPackage.exe (средство командной строки DACFx)**  
  
-   Извлечение DACPAC с данными — создает файл моментального снимка базы данных (DACPAC) из активной базы данных SQL Server или SQL Windows Azure, содержащей данные из пользовательских таблиц в дополнение к схеме базы данных. Эти пакеты могут быть опубликованы в новой или существующей базе данных SQL Server или SQL Windows Azure с помощью действия публикации средства SqlPackage.exe. Данные, содержащиеся в пакете, заменят собой существующие данные в целевой базе данных.  
  
-   Экспортирование BACPAC — создает логический файл резервной копии (BACPAC-файл) из активной базы данных SQL Server или SQL Windows Azure, содержащей схему базы данных и пользовательские данные, которые могут быть использованы для миграции базы данных с сервера SQL Server, находящегося на предприятии, в базу данных SQL Windows Azure. Базы данных, совместимые с Azure, могут передаваться посредством экспорта и импорта между поддерживаемыми версиями SQL Server.  
  
-   Импорт BACPAC — импортирует BACPAC-файл, создавая новую или заполняя пустую базу данных SQL Server или SQL Windows Azure.  
  
Полная документация по SqlPackage.exe на MSDN находится [здесь](http://msdn.microsoft.com/library/hh550080%28v=vs.103%29.aspx).  
  
**Совместимость пакетов**  
  
В этом выпуске вводится несколько сценариев прямой совместимости для пакетов приложения уровня данных.  
  
-   Пакеты приложения уровня данных, созданные этим выпуском и не содержащие элементов SXI и табличных данных, поддерживаются предыдущими выпусками DACFx (SQL Server 2012 RTM, SQL Server 2012 CU1 и DACFx September, 2012).  
  
-   Все пакеты приложения уровня данных, созданные предыдущими версиями DACFx, поддерживаются этим выпуском.  
  
## <a name="bkmk_known_issues_fixed"></a>8.0 Известные проблемы, исправленные в этом пакете обновления  
Полный список ошибок и известных проблем, исправленных в этом пакете обновления, см. в [статье базы знаний](http://support.microsoft.com/kb/2674319).  
  
[Содержание](#bkmk_top)  
  
## <a name="see-also"></a>См. также:  
[Как определить версию и выпуск SQL Server](http://support.microsoft.com/kb/321185)  
[Возможности, поддерживаемые различными выпусками SQL Server 2014](http://msdn.microsoft.com/en-us/5da61ff5-12b9-48e6-b3c8-0dacca1751c4)  
  

