---
title: Подготовка к запросу информации об изменениях данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 52e05ac0ddc2f32a8131d2630cd82f8b92c52f07
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35328348"
---
# <a name="prepare-to-query-for-the-change-data"></a>Подготовка к запросу информации об изменениях
  В потоке управления пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , который выполняет добавочную загрузку измененных данных, третья и последняя задача состоит в том, чтобы подготовить запрос для измененных данных и добавить задачу потока данных.  
  
> [!NOTE]  
>  Вторая задача для потока управления — убедиться, что измененные данные для выбранного интервала готовы. Дополнительные сведения об этой задаче см. в разделе [Определение готовности информации об изменениях данных](../../integration-services/change-data-capture/determine-whether-the-change-data-is-ready.md). Описание общего процесса по проектированию потока управления см. в разделе [Система отслеживания измененных данных (SSIS)](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## <a name="design-considerations"></a>Вопросы проектирования  
 Чтобы получить измененные данные, нужно вызвать возвращающую табличное значение функцию Transact-SQL, которая принимает конечные точки интервала в качестве входных параметров и возвращает измененные данные за указанный период. Эту функцию вызывает исходный компонент в потоке данных. Сведения об этом исходном компоненте см. в разделе [Получение и интерпретация измененных данных](../../integration-services/change-data-capture/retrieve-and-understand-the-change-data.md).  
  
 Чаще всего используемые исходные компоненты служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , включая источник OLE DB, источник ADO и источник ADO NET, не могут получить сведения о параметрах для функции с табличным значением. Следовательно, в большинстве своем источники не могут вызывать параметризованные функции напрямую.  
  
 Существует два конструкторских решения проблемы передачи входных параметров для такой функции.  
  
-   **Сборка параметризированного запроса в виде строки**. Чтобы собрать динамическую строку SQL со значениями параметров, жестко запрограммированными в эту строку, можно использовать задачу «Скрипт» или «Выполнение SQL». Затем эту строку можно сохранить в переменной пакета и использовать для задания исходному компоненту свойства SqlCommand. Этот подход приводит к успеху, так как исходный компонент более не требует сведений о параметрах.  
  
    > [!NOTE]  
    >  Выполнение предварительно скомпилированных скриптов требует меньше ресурсов, чем использование задачи «Выполнение SQL».  
  
-   **Использование параметризованной оболочки**. В качестве альтернативы можно создать параметризованную хранимую процедуру как оболочку, которая вызывает параметризованную функцию с табличным значением. Этот подход приводит к успеху, так как исходный компонент может успешно получать сведения о параметрах для хранимой процедуры.  
  
 В данном разделе используется первое конструкторское решение и создается параметризированный запрос в виде строки.  
  
## <a name="preparing-the-query"></a>Подготовка запроса  
 Чтобы получить возможность объединения входных параметров в единую строку запроса, пользователь должен настроить переменные пакета, необходимые для этого запроса.  
  
#### <a name="to-set-up-package-variables"></a>Настройка переменных пакета  
  
-   В окне [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Переменные **среды** создайте переменную со строковым типом данных для хранения строки запроса, возвращенной задачей «Выполнение SQL».  
  
     В этом примере используется имя переменной SqlDataQuery.  
  
 После создания переменной пакета можно объединять значения входных параметров с помощью задачи «Скрипт» или «Выполнение SQL». В следующих двух процедурах описывается настройка этих компонентов.  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a>Использование задачи «Скрипт» для объединения строки запроса  
  
1.  На вкладке **Поток управления** добавьте к пакету задачу «Скрипт» после контейнера «цикл по элементам» и соедините контейнер с этой задачей.  
  
    > [!NOTE]  
    >  Здесь предполагается, что пакет выполняет добавочную загрузку из одной таблицы. Если пакет загружает данные из нескольких таблиц и содержит родительский пакет с несколькими дочерними, то эту задачу следует добавить в качестве первого компонента каждого из дочерних пакетов. Дополнительные сведения см. в разделе [Выполнение добавочной загрузки нескольких таблиц](../../integration-services/change-data-capture/perform-an-incremental-load-of-multiple-tables.md).  
  
2.  В окне **Редактор задачи «Скрипт»** на странице **Скрипт** выберите следующие параметры.  
  
    1.  Для свойства **ReadOnlyVariables**выберите из списка значения **User::DataReady**, **User::ExtractStartTime**и **User::ExtractEndTime** .  
  
    2.  Для свойства **ReadWriteVariables**выберите из списка значение User::SqlDataQuery.  
  
3.  В окне **Редактор задачи «Скрипт»** на странице **Скрипт** нажмите кнопку **Изменить скрипт** , чтобы открыть среду разработки скриптов.  
  
4.  В главной процедуре введите один из следующих сегментов кода.  
  
    -   При программировании на языке C# введите следующие строки кода:  
  
        ```csharp 
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         \- или -  
  
    -   При программировании на языке [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], введите следующие строки кода:  
  
        ```vb  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  Оставьте без изменений создаваемую по умолчанию строку кода, которая возвращает **DtsExecResult.Success** в результате выполнения скрипта.  
  
6.  Закройте среду разработки скриптов и **Редактор задачи «Скрипт»**.  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a>Использование задачи «Выполнение SQL» для объединения строки запроса  
  
1.  На вкладке **Поток управления** добавьте к пакету задачу «Выполнение SQL» после контейнера «цикл по элементам» и соедините контейнер с этой задачей.  
  
    > [!NOTE]  
    >  Здесь предполагается, что пакет выполняет добавочную загрузку из одной таблицы. Если пакет загружает данные из нескольких таблиц и содержит родительский пакет с несколькими дочерними, то эту задачу следует добавить в качестве первого компонента каждого из дочерних пакетов. Дополнительные сведения см. в разделе [Выполнение добавочной загрузки нескольких таблиц](../../integration-services/change-data-capture/perform-an-incremental-load-of-multiple-tables.md).  
  
2.  В окне **Редактор задачи «Выполнение SQL»** на странице **Общие** выберите следующие параметры:  
  
    1.  Для параметра **ResultSet**выберите значение **Одна строка**.  
  
    2.  Настройте допустимое соединение с базой данных-источником.  
  
    3.  Для параметра **SQLSourceType**выберите значение **Прямой ввод**.  
  
    4.  В поле **SQLStatement**введите приведенную ниже инструкцию SQL:  
  
        ```sql
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  Предложение **else** в этом образце формирует запрос на первоначальную загрузку информации об изменениях, передавая значение NULL для даты и времени начала. Этот образец не учитывает случай, когда изменения, сделанные до включения системы отслеживания измененных данных, тоже необходимо загрузить в хранилище данных.  
  
3.  На странице **Сопоставление параметров** средства **Редактор задачи «Выполнение SQL»** выполните следующее сопоставление.  
  
    1.  Сопоставьте переменную DataReady с параметром 0.  
  
    2.  Сопоставьте переменную ExtractStartTime с параметром 1.  
  
    3.  Сопоставьте переменную ExtractEndTime с параметром 2.  
  
4.  На странице **Результирующий набор** средства **Редактор задачи «Выполнение SQL»** сопоставьте столбец «Имя результата» с переменной SqlDataQuery.  
  
     Имя результата — это имя единственного возвращаемого столбца SqlDataQuery.  
  
 Предшествующие процедуры настраивают задачу, которая готовит строку запроса с жестко запрограммированными строковыми значениями для входных параметров. Следующий код представляет собой пример такой строки запроса:  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a>Добавление задачи потока данных  
 Последний этап процесса разработки потока управления для пакета — добавление задачи потока данных.  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a>Добавление задачи потока данных и завершение формирования потока управления  
  
-   На вкладке **Поток управления** добавьте задачу потока данных и соедините с задачей, которая объединяла строку запроса.  
  
## <a name="next-step"></a>Следующий шаг  
 Завершив подготовку строки запроса и настройку задачи потока данных, приступайте к следующему шагу — созданию функции с табличным значением для получения измененных данных из базы данных.  
  
 **Следующий раздел:** [Создание функции для получения измененных данных](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md)  
  
  
