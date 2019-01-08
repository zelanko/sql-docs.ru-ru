---
title: Установить поставщик OLE DB служб Analysis Services на серверах SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c24c5f07d18bc8d63ff0d113c762f776dccf9a41
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53376646"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>Установка поставщика OLE DB служб Analysis Services на серверах SharePoint
  Поставщик Microsoft OLE DB для служб Analysis Services (MSOLAP) представляет собой интерфейс, используемый клиентскими приложениями для взаимодействия с данными служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. В среде SharePoint, где установлен [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], поставщик обрабатывает запросы на подключение к данным [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
 Поставщик данных включен в пакет установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi), но, возможно, потребуется и ручная установка. Существует две причины, по которым может потребоваться установить клиентские библиотеки или поставщики данных вручную на сервер SharePoint.  
  
-   **Обеспечение обратной совместимости**. Книги [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] указывают версию [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] поставщика OLE DB служб Analysis Services в своей строке подключения. В связи с этим для успешного выполнения запроса на компьютере должна присутствовать эта версия поставщика.  
  
-   **Включение доступа к данным на выделенном экземпляре служб Excel Services**. Если в ферме SharePoint есть службы Excel Services на сервере, на котором нет [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], необходимо установить версию [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] поставщика и другие компоненты для обеспечения связи с клиентами с помощью пакета установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].  
  
    > [!NOTE]  
    >  Эти ситуации не являются взаимоисключающими. Для размещения книг нескольких версий в ферме, в которой есть серверы приложений, использующие службы Excel Services без экземпляра [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], потребуется установить и старые и новые версии поставщика данных на каждый компьютер со службами Excel Services.  
  
  
##  <a name="bkmk_vers"></a> Версии поставщика OLE DB, которые поддерживают доступ к данным PowerPivot  
 Ферма SharePoint может включать несколько версий поставщика OLE DB служб Analysis Services, включая предыдущие версии, которые не поддерживают доступ к данным PowerPivot.  
  
 По умолчанию вместе с SharePoint 2010 устанавливается версия [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] поставщика. Хотя он определяется как MSOLAP.4 (та же версия, которая используется для [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]), данная версия не работает для доступа к данным PowerPivot. Чтобы успешно установить соединение, необходима версия [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] или [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поставщика.  
  
 Следующая за [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] версия поставщика OLE DB включает новые средства поддержки транспорта и соединений для структур данных служб [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]. В книгах [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] используются новые версии поставщика для передачи запросов на обработку серверам [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме. Чтобы получить обновленную версию, можно загрузить ее и установить с помощью страницы «Пакет дополнительных компонентов SQL Server».  
  
 В следующей таблице описаны допустимые значения.  
  
|Версия продукта|Версия файла|Действует для:|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|MSOLAP100.dll в файловой системе<br /><br /> MSOLAP.4 в строке подключения Excel<br /><br /> 10.50.1600 или выше в подробных сведениях о версии файла|Используется для моделей данных, созданных с помощью надстройки PowerPivot для Excel версии [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|MSOLAP110.dll в файловой системе<br /><br /> MSOLAP.5 в строке подключения Excel<br /><br /> 11.0.0000 или выше в подробных сведениях о версии файла|Используется для моделей данных, созданных с помощью [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] для Excel версии [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|MSOLAP120.dll в файловой системе<br /><br /> 12.0.20000 или выше в подробных сведениях о версии файла|Используется для моделей данных, отличных от моделей [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
  
  
##  <a name="bkmk_why"></a> Почему необходимо установить поставщик OLE DB  
 Встречаются две ситуации, которые могут вызвать необходимость установки поставщика OLE DB на серверах фермы вручную.  
  
 **Наиболее распространенным сценарием** при наличии более старых и новых версиях [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] книг, которые сохраняются в библиотеках фермы документов. Если аналитики организации пользуются надстройкой [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] версии [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel и сохраняют такие книги в установке [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], то старые книги работать не будут. Ее строка подключения будет ссылаться на более старую версию поставщика, который не будет находиться на сервере, если не установить его. Установка обеих версий поможет обеспечить доступ к данным в книгах PowerPivot, созданных и в старых и в новых версиях надстройки [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] для Excel. Программа установки [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] не устанавливает версию [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] поставщика, поэтому его необходимо установить вручную, чтобы обеспечить доступ к книгам из предыдущей версии.  
  
 **Во втором сценарии** при наличии сервера в ферме SharePoint, на котором запущены службы Excel, но не [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)]. В этом случае сервер приложений, на котором запускаются службы Excel, должен быть обновлен вручную для использования новой версии поставщика. Это необходимо для соединения с экземпляром PowerPivot для SharePoint. Если службы Excel Services используют старую версия поставщика, запрос на соединение выполнить не удастся. Обратите внимание, что поставщик должен быть установлен с помощью мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или пакета установки [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] (spPowerPivot.msi), чтобы были установлены поддерживающие элементы для всех компонентов [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].  
  
  
##  <a name="bkmk_sql11"></a> Установить SQL Server 2012 поставщика OLE DB на сервере служб Excel Services с помощью программы установки SQL Server  
 Следующие инструкции помогут установить поставщик OLE DB и другие компоненты для обеспечения связи с клиентами на серверах SharePoint, где он еще не установлен, например на серверах приложений, где службы Excel Services работают без надстройки PowerPivot для SharePoint.  
  
 Используйте эти инструкции для установки текущего поставщика OLE DB служб Analysis Services и добавления **Microsoft.AnalysisServices.Xmla.dll** к глобальной сборке.  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>Запуск программы установки SQL Server и установка клиентских средств подключения  
  
1.  На сервере приложений, где размещены службы Excel Services, запустите программу установки SQL Server.  
  
2.  На странице установки выберите **автономная установка нового SQL Server или добавление компонентов к существующей установке**.  
  
3.  На странице «тип установки» выберите **выполнить новую установку SQL Server 2012**.  
  
4.  На странице «роль установки» выберите **Установка компонентов SQL Server**.  
  
5.  На **Выбор компонентов** щелкните **средства связи клиентских средств**. Этот параметр устанавливает **Microsoft.AnalysisServices.Xmla.dll**  
  
     Не выбирайте другие функции.  
  
6.  Нажмите кнопку **Далее** завершите работу мастера, а затем нажмите кнопку **установить** для запуска программы установки.  
  
7.  При наличии других серверов со службами Excel Services, на которых не установлена надстройка PowerPivot для SharePoint, повторите описанные выше шаги.  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>Убедитесь в том, что MSOLAP.5 является надежным поставщиком  
  
1.  В центре администрирования выберите **Управление приложениями служб**и щелкните приложение служб Excel Services.  
  
2.  Щелкните **Надежные поставщики данных**.  
  
3.  Убедитесь, что в списке отображается MSOLAP.5. MSOLAP.5 уже может быть надежным поставщиком, в зависимости от настройки PowerPivot для SharePoint. Если вы использовали средство конфигурации PowerPivot, а затем выполнили это действие из списка задач, поставщик MSOLAP.5 не будет надежным для служб Excel Services. В этом случае его необходимо будет добавить вручную.  
  
4.  Если MSOLAP отсутствует в списке, нажмите кнопку **добавить надежный поставщик данных**.  
  
5.  В качестве идентификатора поставщика введите `MSOLAP.5`.  
  
6.  В качестве типа поставщика необходимо указать OLE DB.  
  
7.  В поле "Описание поставщика" введите **Поставщик Microsoft OLE DB для OLAP Services 11.0**.  
  
#### <a name="verify-installation"></a>Проверка установки  
  
1.  Перейдите в каталог «Program Files\Microsoft Analysis Services\AS OLEDB\110».  
  
2.  Щелкните правой кнопкой мыши файл msolap110.dll и выберите пункт **Свойства**.  
  
3.  Щелкните **Сведения**.  
  
4.  Просмотрите информацию о версии файла. Номер версии должен содержать 11.00. \<buildnumber >.  
  
5.  Удостоверьтесь, что в папке «Windows\assembly» присутствует файл Microsoft.AnalysisServices.Xmla.dll версии 11.0.0.0.  
  
  
##  <a name="bkmk_install2012_from_sppowerpivot_msi"></a> Используйте PowerPivot для пакета установки SharePoint (spPowerPivot.msi) для установки SQL Server 2012 поставщика OLE DB  
 Установка [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] поставщика OLE DB на и сервер служб Excel с помощью [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] пакет установки **(spPowerPivot.msi)**.  
  
#### <a name="download-the-msolap5-provider-from-the-includesssql11sp1includessssql11sp1-mdmd-feature-pack"></a>Загрузите поставщик MSOLAP.5 из пакета дополнительных компонентов [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] .  
  
1.  Перейдите к [Microsoft® SQL Server® 2012 SP1 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35580)  
  
2.  Нажмите кнопку **инструкции по установке**.  
  
3.  См. в разделе «Microsoft Analysis Services OLE DB поставщика для Microsoft SQL Server 2012 SP1». Загрузите файл и начните установку.  
  
4.  На **Выбор компонентов** выберите **поставщик Analysis Services OLE DB для SQL Server**. Снимите флажки с других компонентов и завершите установку. Дополнительные сведения о spPowerPivot.msi см. в разделе [установки или удаления PowerPivot для SharePoint надстройка &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
5.  Зарегистрируйте MSOLAP.5 в качестве надежного поставщика в службах Excel SharePoint. Дополнительные сведения см. в разделе [Добавление MSOLAP.5 в качестве надежного поставщика данных в службах Excel Services](https://technet.microsoft.com/library/hh758436.aspx).  
  
  
##  <a name="bkmk_kj"></a> Установите поставщик SQL Server 2008 R2 OLE DB для размещения более ранней версии книги  
 Используйте следующие инструкции, чтобы установить версию [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] поставщика MSOLAP.4 и зарегистрировать файл Microsoft.AnalysisServices.ChannelTransport.dll. ChannelTransport является дочерним компонентом поставщика OLE DB служб Analysis Services. Версия [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] поставщика читает реестр с помощью метода ChannelTransport для установления подключения. Регистрация этого файла после выполнения установки требуется только для тех соединений, которые обрабатываются поставщиком [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] на сервере [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
#### <a name="step-1-download-and-install-the-client-library"></a>Шаг 1. Загрузка и установка клиентской библиотеки  
  
1.  На [страницы пакета дополнительных компонентов SQL Server 2008 R2](https://go.microsoft.com/fwlink/?LinkId=159570), найти поставщик Microsoft Analysis Services OLE DB для Microsoft SQL Server 2008 R2.  
  
2.  Загрузите пакет x64 программы установки `SQLServer2008_ASOLEDB10.msi`. Несмотря на то что в имени содержится SQLServer2008, это правильный файл для поставщика версии SQL Server 2008 R2.  
  
3.  На компьютере, где имеется установка [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)], запустите файл MSI, чтобы установить библиотеку.  
  
4.  Если в ферме есть другие серверы, которые используют только службы Excel Services, без [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] на том же компьютере, повторите предыдущие шаги, чтобы установить версию 2008 R2 поставщика на компьютер со службами Excel Services.  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>Этап 2. Зарегистрируйте файл Microsoft.AnalysisServices.ChannelTransport.dll  
  
1.  Используйте программу regasm.exe для регистрации файла. Если вы не использовали программу regasm.exe перед, добавьте ее родительскую папку, C:\Windows\Microsoft.NET\Framework64\v4.0.30319\\, переменную системного пути.  
  
2.  Откройте командную строку с разрешениями администратора.  
  
3.  Перейдите в папку «С:\Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91»  
  
4.  Введите следующую команду: `regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  Повторите предыдущие шаги для любого компьютера, на который вручную установили версию 2008 R2 поставщика.  
  
#### <a name="verify-installation"></a>Проверка установки  
  
1.  Теперь можно делать срезы или фильтровать книги [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]. Если возникает какая-либо ошибка, убедитесь, что для регистрации файла вы использовали 64-разрядную версию программы regasm.exe.  
  
2.  Кроме того, вы можете проверить версию файла.  
  
     Перейдите к `C:\Program files\Microsoft Analysis Services\AS OLEDB\10`. Щелкните правой кнопкой мыши **msolap100.dll** и выберите **свойства**. Щелкните **Сведения**.  
  
     Просмотрите информацию о версии файла. Номер версии должен содержать 10.50. \<buildnumber >.  
  
  
## <a name="see-also"></a>См. также  
 [Установка PowerPivot для SharePoint 2010](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
