---
title: Практическое руководство. Написание модульного теста SQL Server, который выполняется в области действия одной транзакции | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cb241e94-d81c-40e9-a7ae-127762a6b855
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b20a2432ae509923b2befd240a66de04c50502c4
ms.sourcegitcommit: b8e2e3e6e04368aac54100c403cc15fd4e4ec13a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45564130"
---
# <a name="how-to-write-a-sql-server-unit-test-that-runs-within-the-scope-of-a-single-transaction"></a>Практическое руководство. Написание модульного теста SQL Server, который выполняется в области действия одной транзакции
Можно изменить модульные тесты для запуска в области действия одной транзакции. При использовании этого подхода после завершения теста реализованные им изменения можно будет отменить. Приведенные ниже инструкции показывают, как выполнить следующие задачи.  
  
-   Создайте транзакцию в тестовом скрипте Transact\-SQL с инструкциями **BEGIN TRANSACTION** и **ROLLBACK TRANSACTION**.  
  
-   Создать транзакцию для одного метода теста в классе тестов.  
  
-   Создать транзакцию для всех методов теста в классе тестов.  
  
**Предварительные требования**  
  
Для некоторых процедур, описанных в этом разделе, на компьютере, где запускаются модульные тесты, должна быть запущена служба координатора распределенных транзакций. Дополнительные сведения см. в инструкциях в конце этого раздела.  
  
## <a name="to-create-a-transaction-using-transact-sql"></a>Создание транзакции с помощью Transact\-SQL  
  
#### <a name="to-create-a-transaction-using-transact-sql"></a>Создание транзакции с помощью Transact\-SQL  
  
1.  Откройте модульный тест конструкторе модульных тестов SQL Server. (Дважды щелкните файл исходного кода, чтобы открыть модульный тест в конструкторе.)  
  
2.  Укажите тип скрипта, для которого необходимо создание транзакции. Например, можно указать скрипты, выполняемые до, во время или после теста.  
  
3.  Введите тестовый скрипт в редакторе Transact\-SQL.  
  
4.  Вставьте инструкции `BEGIN TRANSACTION` и `ROLLBACK TRANSACTION`, как показано в следующем простом примере. В примере используется таблица базы данных OrderDetails, которая содержит 50 строк данных.  
  
    ```  
    BEGIN TRANSACTION TestTransaction  
    UPDATE "OrderDetails" set Quantity = Quantity + 10  
    IF @@ROWCOUNT!=50  
    RAISERROR('Row count does not equal 50',16,1)  
    ROLLBACK TRANSACTION TestTransaction  
    ```  
  
    > [!NOTE]  
    > Отменить транзакции после выполнения инструкции COMMIT TRANSACTION нельзя.  
  
    Дополнительные сведения о том, как инструкция ROLLBACK TRANSACTION работает с хранимыми процедурами и триггерами, см. на следующей странице веб-сайта Майкрософт: [ROLLBACK TRANSACTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=115927).  
  
## <a name="to-create-a-transaction-for-a-single-test-method"></a>Создание транзакции для одного метода теста  
В этом примере при использовании типа [System.Transactions.TransactionScope](https://docs.microsoft.com/dotnet/api/system.transactions.transactionscope) будет задействована внешняя транзакция. По умолчанию соединения для выполнения и привилегированные подключения не используют внешнюю транзакцию, так как они создаются до выполнения этого метода. Соединение SqlConnection имеет метод [System.Data.SqlClient.SqlConnection.EnlistTransaction](https://docs.microsoft.com/dotnet/api/system.data.sqlclient.sqlconnection.enlisttransaction), который связывает активное подключение с транзакцией. При создании внешняя транзакция автоматически регистрируется в качестве текущей транзакции. К ней можно обратиться через свойство [System.Transactions.Transaction.Current](https://docs.microsoft.com/dotnet/api/system.transactions.transaction.current). В этом примере транзакция отменяется при уничтожении внешней транзакции. Чтобы зафиксировать изменения, внесенные при запуске модульного теста, используйте метод [System.Transactions.TransactionScope.Complete](https://docs.microsoft.com/dotnet/api/system.transactions.transactionscope.complete).  
  
#### <a name="to-create-a-transaction-for-a-single-test-method"></a>Создание транзакции для одного метода теста  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши узел **Ссылки** в тестовом проекте и выберите пункт **Добавить ссылку**.  
  
    Откроется диалоговое окно **Добавление ссылки**.  
  
2.  Перейдите на вкладку **.NET**.  
  
3.  В списке сборок выберите **System.Transactions** и щелкните **ОК**.  
  
4.  Откройте файл Visual Basic или C# для модульного теста.  
  
5.  Инкапсулируйте действия, выполняемые до, во время и после теста, как показано в следующем примере кода на языке Visual Basic.  
  
    ```  
    <TestMethod()> _  
    Public Sub dbo_InsertTable1Test()  
  
        Using ts as New System.Transactions.TransactionScope( System.Transactions.TransactionScopeOption.Required)  
            ExecutionContext.Connection.EnlistTransaction(Transaction.Current)  
            PrivilegedContext.Connection.EnlistTransaction(Transaction.Current)  
  
            Dim testActions As DatabaseTestActions = Me.dbo_InsertTable1TestData  
            'Execute the pre-test script  
            '  
            System.Diagnostics.Trace.WriteLineIf((Not (testActions.PretestAction) Is Nothing), "Executing pre-test script...")  
            Dim pretestResults() As ExecutionResult = TestService.Execute(Me.PrivilegedContext, Me.PrivilegedContext, testActions.PretestAction)  
            'Execute the test script  
  
            System.Diagnostics.Trace.WriteLineIf((Not (testActions.TestAction) Is Nothing), "Executing test script...")  
            Dim testResults() As ExecutionResult = TestService.Execute(ExecutionContext, Me.PrivilegedContext, testActions.TestAction)  
  
            'Execute the post-test script  
            '  
            System.Diagnostics.Trace.WriteLineIf((Not (testActions.PosttestAction) Is Nothing), "Executing post-test script...")  
            Dim posttestResults() As ExecutionResult = TestService.Execute(Me.PrivilegedContext, Me.PrivilegedContext, testActions.PosttestAction)  
  
            'Because the transaction is not explicitly committed, it  
            'is rolled back when the ambient transaction is   
            'disposed.  
            'To commit the transaction, remove the comment delimiter  
            'from the following statement:  
            'ts.Complete()  
  
    End Sub  
    Private dbo_InsertTable1TestData As DatabaseTestActions  
    ```  
  
    > [!NOTE]  
    > Если вы используете Visual Basic, добавьте инструкцию `Imports System.Transactions` в дополнение к `Imports Microsoft.VisualStudio.TestTools.UnitTesting`, `Imports Microsoft.VisualStudio.TeamSystem.Data.UnitTesting` и `Imports Microsoft.VisualStudio.TeamSystem.Data.UnitTest.Conditions`. Если используется Visual C#, добавьте инструкцию `using System.Transactions` в дополнение к инструкциям `using` в Microsoft.VisualStudio.TestTools, Microsoft.VisualStudio.TeamSystem.Data.UnitTesting и Microsoft.VisualStudio.TeamSystem.Data.UnitTesting.Conditions. В проект также необходимо добавить ссылки на эти сборки.  
  
## <a name="to-create-a-transaction-for-all-test-methods-in-a-test-class"></a>Создание транзакции для всех методов теста в классе тестов  
  
#### <a name="to-create-a-transaction-for-all-test-methods-in-a-test-class"></a>Создание транзакции для всех методов теста в классе тестов  
  
1.  Откройте файл Visual Basic или C# для модульного теста.  
  
2.  Создайте транзакцию в методе TestInitialize и уничтожьте ее в методе TestCleanup, как показано в следующем примере кода для Visual C#.  
  
    ```  
    TransactionScope _trans;  
  
            [TestInitialize()]  
            public void Init()  
            {  
                _trans = new TransactionScope();  
                base.InitializeTest();  
            }  
  
            [TestCleanup()]  
            public void Cleanup()  
            {  
                base.CleanupTest();  
                _trans.Dispose();  
            }  
  
            [TestMethod()]  
            public void TransactedTest()  
            {  
                DatabaseTestActions testActions = this.DatabaseTestMethod1Data;  
                // Execute the pre-test script  
                //   
                System.Diagnostics.Trace.WriteLineIf((testActions.PretestAction != null), "Executing pre-test script...");  
                ExecutionResult[] pretestResults = TestService.Execute(this.PrivilegedContext, this.PrivilegedContext, testActions.PretestAction);  
                // Execute the test script  
                //   
                System.Diagnostics.Trace.WriteLineIf((testActions.TestAction != null), "Executing test script...");  
                ExecutionResult[] testResults = TestService.Execute(this.ExecutionContext, this.PrivilegedContext, testActions.TestAction);  
                // Execute the post-test script  
                //   
                System.Diagnostics.Trace.WriteLineIf((testActions.PosttestAction != null), "Executing post-test script...");  
                ExecutionResult[] posttestResults = TestService.Execute(this.PrivilegedContext, this.PrivilegedContext, testActions.PosttestAction);  
  
            }  
    ```  
  
## <a name="to-start-the-distributed-transaction-coordinator-service"></a>Запуск службы координатора распределенных транзакций  
В некоторых процедурах, описанных в данном разделе, используются типы из сборки System.Transactions. При запуске модульных тестов, прежде чем выполнять эти процедуры, необходимо убедиться в том, что служба координатора распределенных транзакций запущена на компьютере. В противном случае тесты будут завершаться следующей ошибкой: "Метод теста *имя_проекта*.*имя_теста*.*имя_метода* вызвал исключение: System.Data.SqlClient.SqlException: MSDTC на сервере "*имя_компьютера*" недоступен".  
  
#### <a name="to-start-the-distributed-transaction-coordinator-service"></a>Запуск службы координатора распределенных транзакций  
  
1.  Откройте **Панель управления**.  
  
2.  На **панели управления** выберите пункт **Средства администрирования**.  
  
3.  В окне **Средства администрирования** выберите **Службы**.  
  
4.  На панели **Службы** щелкните правой кнопкой мыши службу **Контроллер распределенных транзакций** и выберите **Пуск**.  
  
    Состояние службы должно смениться на **Запущена**. Теперь можно запускать модульные тесты, использующие System.Transactions.  
  
> [!IMPORTANT]  
> Даже если служба контроллера распределенных транзакций запущена, может возникнуть следующая ошибка: `System.Transactions.TransactionManagerCommunicationException: Network access for Distributed Transaction Manager (MSDTC) has been disabled. Please enable DTC for network access in the security configuration for MSDTC using the Component Services Administrative tool. ---> System.Runtime.InteropServices.COMException: The transaction manager has disabled its support for remote/network transactions. (Exception from HRESULT: 0x8004D024)`. Если выдается эта ошибка, то необходимо настроить сетевой доступ для службы контроллера распределенных транзакций. Дополнительные сведения см. в статье о [включении сетевого доступа DTC](http://go.microsoft.com/fwlink/?LinkId=193916).  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
  
