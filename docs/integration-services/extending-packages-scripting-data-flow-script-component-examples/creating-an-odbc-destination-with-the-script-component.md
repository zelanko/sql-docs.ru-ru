---
title: "Создание назначения ODBC с помощью компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5eb539f0d18f473b10ed8d49bcee9c298292fb41
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>Создание назначения ODBC с помощью компонента скрипта
  В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], как правило, сохранение данных в назначение ODBC с помощью [!INCLUDE[vstecado](../../includes/vstecado-md.md)] назначения и [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] поставщик данных для ODBC. Однако можно также создать нерегламентированное назначение ODBC для использования в отдельном пакете. Для создания такого нерегламентированного назначения ODBC используется компонент скрипта, показанный в следующем примере.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как создать целевой компонент, который использует ODBC существующий диспетчер соединений для сохранения данных из потока данных в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы.  
  
 В этом примере, является модификацией пользовательской [!INCLUDE[vstecado](../../includes/vstecado-md.md)] назначения, приведенного ранее в разделе [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Однако в данном примере пользовательское назначение [!INCLUDE[vstecado](../../includes/vstecado-md.md)] изменено для работы с диспетчером соединений ODBC и сохранения данных в назначение ODBC. Были внесены, в частности, следующие изменения:  
  
-   Не удается вызвать **AcquireConnection** диспетчера соединений ODBC из управляемого кода, поскольку он возвращает собственный объект. Поэтому в данном образце строка соединения диспетчера соединений используется для соединения с источником данных непосредственно с помощью управляемого поставщика данных ODBC платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   **OdbcCommand** ожидает позиционированных параметров. Позиции параметров отмечаются вопросительными знаками (?) в тексте команды. (В отличие от этого **SqlCommand** ожидает именованных параметров.)  
  
 В этом примере используется **Person.Address** в таблицу **AdventureWorks** образца базы данных. В примере передается первый и четвертый столбец  **int*AddressID*** и **Город nvarchar (30)** столбцы этой таблицы данных в потоке. Тех же данных используется в источнике, преобразования и назначения образцы в разделе [разработка определенных типов компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Создайте соединение диспетчера соединений ODBC **AdventureWorks** базы данных.  
  
2.  Создайте целевую таблицу, выполнив следующую команду Transact-SQL в **AdventureWorks** базы данных:  
  
    ```sql
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
4.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Чтобы обеспечить работу этого образца, необходимо включить в выход вышестоящего компонента по крайней мере **AddressID** и **Город** столбцы из **Person.Address** таблицу **AdventureWorks** образца базы данных.  
  
5.  Откройте **редактор преобразования «скрипт»**. На **входные столбцы** выберите **AddressID** и **Город** столбцов.  
  
6.  На **входы и выходы** страницы, например, измените имя входа на более описательное имя **MyAddressInput**.  
  
7.  На **диспетчеры соединений** добавьте или создать диспетчер соединений ODBC с описательным именем, например **MyODBCConnectionManager**.  
  
8.  На **сценарий** нажмите кнопку **изменить скрипт**, а затем введите следующий код в **ScriptMain** класса.  
  
9. Закройте среду разработки скриптов, закройте **редактор преобразования «скрипт»**, а затем выполните образец.  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Создание назначения с помощью компонента скрипта](../../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
