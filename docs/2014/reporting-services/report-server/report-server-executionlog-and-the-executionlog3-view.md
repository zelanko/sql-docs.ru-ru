---
title: Отчет журнала выполнения сервера и представление ExecutionLog3 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], execution
- execution logs [Reporting Services]
ms.assetid: a7ead67d-1404-4e67-97e7-4c7b0d942070
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e8e2f2a714aad9d1824f2ad922b63cd94f2a96d8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63190917"
---
# <a name="report-server-execution-log-and-the-executionlog3-view"></a>Журнал выполнения сервера отчетов и представление ExecutionLog3
  Журнал выполнения для сервера отчетов содержит сведения об отчетах, выполняемых на сервере или на нескольких серверах при использовании масштабного развертывания в собственном режиме или фермы SharePoint. Журнал выполнения отчетов можно использовать для изучения частоты, с которой запрашивается отчет, частоты использования различных форматов вывода и времени обработки в миллисекундах, занимаемого каждой фазой обработки. Журнал содержит сведения о продолжительности времени, затраченного на выполнение запроса набора данных отчета, и времени, затраченного на обработку данных. Администраторы сервера отчетов могут просматривать информацию журнала, выявлять задачи, выполняющиеся продолжительное время, и вносить предложения для разработчиков отчетов в тех областях организации отчета (набор данных или обработка), в которых они могут проводить улучшения.  
  
 На серверах отчетов, настроенных для режима SharePoint, можно также использовать журналы ULS SharePoint. Дополнительные сведения см. в разделе [Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)  
  
##  <a name="bkmk_top"></a> Просмотр данных журнала  
 Сервер отчетов записывает данные о выполнении отчетов во внутреннюю таблицу базы данных. Сведения, содержащиеся в этой таблице, могут быть получены из представлений SQL Server.  
  
 Журнал выполнения отчета хранится в базе данных сервера отчетов, которая по умолчанию носит имя **ReportServer**. Представления SQL отображают сведения журналов выполнения. Представления "2" и "3" были добавлены в последних выпусках и содержат новые поля или поля с более удобными именами, чем в предыдущих выпусках. Существовавшие ранее представления не исключены из состава продукта, поэтому зависящие от них пользовательские приложения не затрагиваются. При отсутствии зависимости от более старого представления, например ExecutionLog, рекомендуется использовать последнее по времени представление, ExecutionLog**3**.  
  
 В этом разделе:  
  
-   [Значения параметров конфигурации для сервера отчетов с режимом SharePoint](#bkmk_sharepoint)  
  
-   [Значения параметров конфигурации для сервера отчетов с собственным режимом](#bkmk_native)  
  
-   [Поля журнала (ExecutionLog3)](#bkmk_executionlog3)  
  
-   [Поле AdditionalInfo](#bkmk_additionalinfo)  
  
-   [Поля журнала (ExecutionLog2)](#bkmk_executionlog2)  
  
-   [Поля журнала (ExecutionLog)](#bkmk_executionlog)  
  
##  <a name="bkmk_sharepoint"></a> Значения параметров конфигурации для сервера отчетов с режимом SharePoint  
 Предусмотрена возможность включать и отключать ведение журнала выполнения отчета с помощью параметров настройки системы для приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 По умолчанию записи журнала хранятся 60 суток. Записи с истекшим сроком хранения удаляются в 02:00 ежедневно. При готовой установке в заданный момент времени доступны данные только за последние 60 дней.  
  
 Возможность ограничения количества строк или типа элементов, вносимых в журнал, отсутствует.  
  
 **Включение ведения журнала выполнения.**  
  
1.  В центре администрирования SharePoint щелкните **Управление приложениями службы** в группе **Управление приложениями** .  
  
2.  Щелкните имя приложения службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , которое требуется настроить.  
  
3.  Нажмите кнопку **Системные параметры**.  
  
4.  Выберите **Включить ведение журнала выполнения** в разделе **Ведение журнала** .  
  
5.  Нажмите кнопку **ОК**.  
  
 **Включение подробного ведения журнала.**  
  
 Необходимо включить ведение журнала, как описано в предыдущих шагах, а затем выполнить следующее:  
  
1.  На странице **Системные параметры** приложения служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] найдите раздел **Определяемые пользователем** .  
  
2.  Измените значение параметра **ExecutionLogLevel** на **подробный**. Это поле представляет собой поле ввода текста, и двумя возможными значениями являются **подробный** и **обычный**.  
  
##  <a name="bkmk_native"></a> Значения параметров конфигурации для сервера отчетов с собственным режимом  
 Предусмотрена возможность включать или отключать ведение журнала выполнения отчета на странице «Свойства сервера» в среде SQL Server Management Studio. Свойство **EnableExecutionLogging** является расширенным.  
  
 По умолчанию записи журнала хранятся 60 суток. Записи с истекшим сроком хранения удаляются в 02:00 ежедневно. При готовой установке в заданный момент времени доступны данные только за последние 60 дней.  
  
 Возможность ограничения количества строк или типа элементов, вносимых в журнал, отсутствует.  
  
 **Включение ведения журнала выполнения.**  
  
1.  Запустите среду SQL Server Management Studio с правами администратора. Например, щелкните правой кнопкой мыши значок среды Management Studio и выберите команду "Запуск от имени администратора".  
  
2.  Установите соединение с требуемым сервером отчетов.  
  
3.  Щелкните правой кнопкой мыши имя сервера и выберите пункт **Свойства**. Если параметр «Свойства» отключен, убедитесь в том, что запуск среды SQL Server Management Studio был выполнен с административными привилегиями.  
  
4.  Перейдите на страницу **Ведение журнала** .  
  
5.  Выберите **Включить ведение журнала выполнения отчета**.  
  
 **Включение подробного ведения журнала.**  
  
 Необходимо включить ведение журнала, как описано в предыдущих шагах, а затем выполнить следующее:  
  
1.  В окне **Свойства сервера** перейдите на страницу **Дополнительно** .  
  
2.  В разделе **Определяемый пользователем** измените значение **ExecutionLogLevel** на **подробный**. Это поле представляет собой поле ввода текста, и двумя возможными значениями являются **подробный** и **обычный**.  
  
##  <a name="bkmk_executionlog3"></a> Поля журнала (ExecutionLog3)  
 Это представление добавило дополнительный узел диагностики производительности в столбец на основе XML **AdditionalInfo** . Столбец AdditionalInfo содержит XML-структуру дополнительных полей данных вида «один ко многим». Ниже приведен пример инструкции Transact SQL для выборки строк из представления ExecutionLog3. В этом образце предполагается, что база данных сервера отчетов носит имя **ReportServer**:  
  
```  
Use ReportServer  
select * from ExecutionLog3 order by TimeStart DESC  
```  
  
 В следующей таблице описаны данные, которые перехватываются в журнале выполнения отчетов  
  
|Столбец|Описание|  
|------------|-----------------|  
|InstanceName|Имя экземпляра сервера отчетов, обработавшего запрос. Если в применяемой среде имеется больше одного сервера отчетов, можно анализировать распределение InstanceName для контроля и определения того, распределяет ли программа уравновешивания сетевой нагрузки запросы по серверам отчетов в соответствии с ожидаемым.|  
|ItemPath|Путь, по которому сохраняется отчет или элемент отчета.|  
|UserName|Идентификатор пользователя.|  
|ExecutionID|Внутренний идентификатор, связанный с запросом. Запросы, выполняемые в рамках одного сеанса пользователя, имеют одинаковый идентификатор выполнения.|  
|RequestType|Возможные значения:<br />**Интерактивный**<br />**Подписка**<br /><br /> <br /><br /> Анализ данных журнала, отфильтрованных по значению RequestType=Subscription и отсортированных по значению TimeStart, может показать периоды интенсивной нагрузки на подписку, и может потребоваться изменить параметры некоторых подписок на отчет для другого вызова.|  
|Формат|Формат подготовки к просмотру.|  
|Параметры|Значения параметров, используемых при выполнении отчета.|  
|ItemAction|Возможные значения:<br /><br /> **Render**<br /><br /> **Sort**<br /><br /> **BookMarkNavigation**<br /><br /> **DocumentNavigation**<br /><br /> **GetDocumentMap**<br /><br /> **Функция FINDSTRING**<br /><br /> **Выполнение**<br /><br /> **RenderEdit**|  
|TimeStart|Время начала и завершения обработки отчета, указывающее на его продолжительность.|  
|TimeEnd||  
|TimeDataRetrieval|Количество миллисекунд, затраченных на выборку данных.|  
|TimeProcessing|Количество миллисекунд, затраченных на обработку отчета.|  
|TimeRendering|Количество миллисекунд, затраченных на подготовку отчета к просмотру.|  
|Source|Источник выполнения отчета. Возможные значения:<br /><br /> **Live**<br /><br /> **Кэш**: Указывает кэшированное выполнение. Например, набор данных, запросы не выполняются немедленно.<br /><br /> **Моментальный снимок**<br /><br /> **Журнал**<br /><br /> **Ad-hoc-** : Указывает либо модели на основе динамически созданный отчет, детализированный отчет, либо отчет в построителе отчетов который просматривается на клиенте с помощью сервера отчетов для обработки и подготовки.<br /><br /> **Сеанс**: Указывает последующий запрос в рамках уже созданного сеанса.  Например, первоначальный запрос был на просмотр страницы 1, а последующий ― на экспорт в Excel с текущим состоянием сеанса.<br /><br /> **RDCE**:  Указывает модуль настройки определения отчета. Пользовательское расширение RDCE позволяет динамически настраивать определение отчета до передачи его в модуль обработки при выполнении отчета.|  
|Состояние|Состояние (либо rsSuccess, либо код ошибки. Если ошибок несколько, то записывается только первая).|  
|ByteCount|Размер отчетов, готовых для просмотра (в байтах).|  
|RowCount|Количество возвращенных по запросам строк.|  
|AdditionalInfo|Контейнер свойств XML, содержащий дополнительные сведения о выполнении. Содержимое может быть разным для каждой строки.|  
  
##  <a name="bkmk_additionalinfo"></a> Поле AdditionalInfo  
 Поле AdditionalInfo представляет собой контейнер свойств XML или структуру, содержащую дополнительные сведения о выполнении. Содержимое может быть разным для каждой строки журнала.  
  
 Следующие таблицы являются примерами содержимого поля AddtionalInfo для стандартного ведения журнала и подробного ведения журнала.  
  
 **Пример столбца AddtionalInfo при стандартном ведении журнала**  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>147</ConnectionOpenTime>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>642</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>63</ExecuteReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>157</TotalTimeDataRetrieval>  
          <ExecuteReaderTime>60</ExecuteReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 **Пример столбца AddtionalInfo при подробном ведении журнала**  
  
```  
<AdditionalInfo>  
  <ProcessingEngine>2</ProcessingEngine>  
  <ScalabilityTime>  
    <Pagination>0</Pagination>  
    <Processing>0</Processing>  
  </ScalabilityTime>  
  <EstimatedMemoryUsageKB>  
    <Pagination>0</Pagination>  
    <Processing>6</Processing>  
  </EstimatedMemoryUsageKB>  
  <DataExtension>  
    <SQL>1</SQL>  
  </DataExtension>  
  <Connections>  
    <Connection>  
      <ConnectionOpenTime>127</ConnectionOpenTime>  
      <DataSource>  
        <Name>DataSource1</Name>  
        <DataExtension>SQL</DataExtension>  
      </DataSource>  
      <DataSets>  
        <DataSet>  
          <Name>DataSet1</Name>  
          <RowsRead>16</RowsRead>  
          <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>33</ExecuteReaderTime>  
          <DataReaderMappingTime>30</DataReaderMappingTime>  
          <DisposeDataReaderTime>1</DisposeDataReaderTime>  
        </DataSet>  
        <DataSet>  
          <Name>DataSet2</Name>  
          <RowsRead>3</RowsRead>  
          <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
          <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
          <ExecuteReaderTime>1</ExecuteReaderTime>  
          <DataReaderMappingTime>0</DataReaderMappingTime>  
          <DisposeDataReaderTime>0</DisposeDataReaderTime>  
        </DataSet>  
      </DataSets>  
    </Connection>  
  </Connections>  
</AdditionalInfo>  
  
```  
  
 Ниже описаны некоторые свойства, которые вы увидите в поле AdditionalInfo.  
  
-   **ProcessingEngine**: 1=SQL Server 2005, 2=новое ядро обработки по требованию. Если в большинстве отчетов все еще отображается значение 1, можно изучить вопрос о том, как их перепроектировать в целях применения более нового и более эффективного ядра обработки по требованию.  
  
     `<ProcessingEngine>2</ProcessingEngine>`  
  
-   **ScalabilityTime**: Количество миллисекунд, затраченных на выполнение операций, связанных с масштабированием, в обрабатывающем ядре. Значение 0 указывает, что на операции масштабирования не было затрачено дополнительное время, а также свидетельствует о том, что запрос не выполнялся в условиях нехватки памяти.  
  
    ```  
    <ScalabilityTime>  
        <Processing>0</Processing>  
    </ScalabilityTime>  
    ```  
  
-   **EstimatedMemoryUsageKB**: Оценка пикового объема памяти в килобайтах, расходуемой каждым компонентом в течение конкретного запроса.  
  
    ```  
    <EstimatedMemoryUsageKB>  
        <Processing>38</Processing>  
    </EstimatedMemoryUsageKB>  
    ```  
  
-   **DataExtension**: Типы модулей обработки данных или источников данных, используемых в отчете. Это число показывает количество вхождений конкретного источника данных.  
  
    ```  
    <DataExtension>  
       <DAX>2</DAX>  
    </DataExtension>  
    ```  
  
-   **ExternalImages**значение указывается в миллисекундах. Эти данные могут использоваться для диагностики проблем производительности. Время, необходимое для получения изображений от внешнего веб-сервера, может замедлить выполнение отчета в целом. Добавлено в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
    ```  
    <ExternalImages>  
        <Count>3</Count>  
        <ByteCount>9268</ByteCount>  
        <ResourceFetchTime>9</ResourceFetchTime>  
    </ExternalImages>  
    ```  
  
-   **Подключения**: Многоуровневая структура. Добавлено в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
    ```  
    <Connections>  
        <Connection>  
          <ConnectionOpenTime>127</ConnectionOpenTime>  
          <DataSource>  
            <Name>DataSource1</Name>  
            <DataExtension>SQL</DataExtension>  
          </DataSource>  
          <DataSets>  
            <DataSet>  
              <Name>DataSet1</Name>  
              <RowsRead>16</RowsRead>  
              <TotalTimeDataRetrieval>655</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>94</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>33</ExecuteReaderTime>  
              <DataReaderMappingTime>30</DataReaderMappingTime>  
              <DisposeDataReaderTime>1</DisposeDataReaderTime>  
            </DataSet>  
            <DataSet>  
              <Name>DataSet2</Name>  
              <RowsRead>3</RowsRead>  
              <TotalTimeDataRetrieval>16</TotalTimeDataRetrieval>  
              <QueryPrepareAndExecutionTime>2</QueryPrepareAndExecutionTime>  
              <ExecuteReaderTime>1</ExecuteReaderTime>  
              <DataReaderMappingTime>0</DataReaderMappingTime>  
              <DisposeDataReaderTime>0</DisposeDataReaderTime>  
            </DataSet>  
          </DataSets>  
        </Connection>  
    </Connections>  
  
    ```  
  
##  <a name="bkmk_executionlog2"></a> Поля журнала (ExecutionLog2)  
 В этом представлении добавлено несколько новых полей, а некоторые другие поля переименованы. Ниже приведен пример инструкции Transact SQL для выборки строк из представления ExecutionLog2. В этом образце предполагается, что база данных сервера отчетов носит имя **ReportServer**:  
  
```  
Use ReportServer  
select * from ExecutionLog2 order by TimeStart DESC  
```  
  
 В следующей таблице описаны данные, которые перехватываются в журнале выполнения отчетов  
  
|Столбец|Описание|  
|------------|-----------------|  
|InstanceName|Имя экземпляра сервера отчетов, обработавшего запрос.|  
|ReportPath|Структура пути к отчету.  Например, отчет с именем test, который находится в корневом каталоге в диспетчере отчетов, будет иметь значение ReportPath, равное "/test".<br /><br /> Отчет с именем test, который сохранен в папке samples в диспетчере отчетов, будет иметь значение ReportPath, равное "/Samples/test/".|  
|UserName|Идентификатор пользователя.|  
|ExecutionID||  
|RequestType|Тип запроса (пользовательский или системный).|  
|Формат|Формат подготовки к просмотру.|  
|Параметры|Значения параметров, используемых при выполнении отчета.|  
|ReportAction|Возможные значения: Render, Sort, BookMarkNavigation, DocumentNavigation, GetDocumentMap, Findstring|  
|TimeStart|Время начала и завершения обработки отчета, указывающее на его продолжительность.|  
|TimeEnd||  
|TimeDataRetrieval|Число миллисекунд, затраченных на получение данных, обработку запроса и его подготовку.|  
|TimeProcessing||  
|TimeRendering||  
|Source|Источник выполнения запроса (1 = напрямую, 2 = кэш, 3 = моментальный снимок, 4 = журнал).|  
|Состояние|Состояние (либо rsSuccess, либо код ошибки. Если ошибок несколько, то записывается только первая).|  
|ByteCount|Размер отчетов, готовых для просмотра (в байтах).|  
|RowCount|Количество возвращенных по запросам строк.|  
|AdditionalInfo|Контейнер свойств XML, содержащий дополнительные сведения о выполнении.|  
  
##  <a name="bkmk_executionlog"></a> Поля журнала (ExecutionLog)  
 Ниже приведен пример инструкции Transact SQL для выборки строк из представления ExecutionLog. В этом образце предполагается, что база данных сервера отчетов носит имя **ReportServer**:  
  
```  
Use ReportServer  
select * from ExecutionLog order by TimeStart DESC  
  
```  
  
 В следующей таблице описаны данные, которые перехватываются в журнале выполнения отчетов  
  
|Столбец|Описание|  
|------------|-----------------|  
|InstanceName|Имя экземпляра сервера отчетов, обработавшего запрос.|  
|ReportID|Идентификатор отчета.|  
|UserName|Идентификатор пользователя.|  
|RequestType|Возможные значения:<br /><br /> True = запрос на подписку<br /><br /> False= интерактивный запрос|  
|Формат|Формат подготовки к просмотру.|  
|Параметры|Значения параметров, используемых при выполнении отчета.|  
|TimeStart|Время начала и завершения обработки отчета, указывающее на его продолжительность.|  
|TimeEnd||  
|TimeDataRetrieval|Число миллисекунд, затраченных на получение данных, обработку запроса и его подготовку.|  
|TimeProcessing||  
|TimeRendering||  
|Source|Источник выполнения отчета. Возможные значения: (1 = реальные данные, 2 = кэш, 3 = моментальный снимок, 4 = журнал, 5 = нерегламентированные данные, 6 = сеанс, 7 = RDCE).|  
|Состояние|Возможные значения: rsSuccess, rsProcessingAborted или код ошибки. Если происходит несколько ошибок, регистрируется только первая ошибка.|  
|ByteCount|Размер отчетов, готовых для просмотра (в байтах).|  
|RowCount|Количество возвращенных по запросам строк.|  
  
## <a name="see-also"></a>См. также:  
 [Включение событий служб Reporting Services для журнала трассировки SharePoint (ULS)](turn-on-reporting-services-events-for-the-sharepoint-trace-log-uls.md)   
 [Файлы и источники журналов служб Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Справочник по ошибкам и событиям (службы Reporting Services)](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
