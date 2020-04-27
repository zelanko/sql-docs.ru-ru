---
title: Создание назначения ODBC с помощью компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5ac76e77d1bd5eebd2e796a6a72463564cb3df3c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62896190"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a>Создание назначения ODBC с помощью компонента скрипта
  В службах [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], как правило, сохранение данных в назначение ODBC осуществляется с использованием назначения [!INCLUDE[vstecado](../../includes/vstecado-md.md)] и поставщика данных платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] для ODBC. Однако можно также создать нерегламентированное назначение ODBC для использования в отдельном пакете. Для создания такого нерегламентированного назначения ODBC используется компонент скрипта, показанный в следующем примере.  
  
> [!NOTE]  
>  Если нужно создать компонент, который будет полезен в нескольких задачах потока данных и нескольких пакетах, рекомендуется в качестве основы использовать этот образец компонента скрипта. Дополнительные сведения см. в разделе [Разработка пользовательского компонента потока данных](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).  
  
## <a name="example"></a>Пример  
 В следующем примере демонстрируется, как создать целевой компонент, который использует существующий диспетчер подключений ODBC для сохранения данных из потока данных в таблицу [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Этот пример представляет собой измененную версию пользовательского назначения [!INCLUDE[vstecado](../../includes/vstecado-md.md)], приведенного ранее в разделе [Создание назначения с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md). Однако в данном примере пользовательское назначение [!INCLUDE[vstecado](../../includes/vstecado-md.md)] изменено для работы с диспетчером соединений ODBC и сохранения данных в назначение ODBC. Были внесены, в частности, следующие изменения:  
  
-   Нельзя вызывать метод `AcquireConnection` диспетчера соединений ODBC из управляемого кода, поскольку при этом возвращается собственный объект. Поэтому в данном образце строка соединения диспетчера соединений используется для соединения с источником данных непосредственно с помощью управляемого поставщика данных ODBC платформы [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
-   Команда `OdbcCommand` ожидает позиционированных параметров. Позиции параметров отмечаются вопросительными знаками (?) в тексте команды. (Команда `SqlCommand`, напротив, ожидает именованных параметров.)  
  
 В этом примере используется таблица **Person.Address** из образца базы данных **AdventureWorks**. В примере в потоке данных передаются первый и четвертый столбцы ( **int * AddressID*** и **nvarchar (30) City)** этой таблицы. Эти же данные используются в образцах источника, преобразования и назначения в разделе [Разработка определенных типов компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).  
  
#### <a name="to-configure-this-script-component-example"></a>Настройка этого примера компонента скрипта  
  
1.  Создайте диспетчер подключений ODBC, который соединяется с базой данных **AdventureWorks**.  
  
2.  Создайте целевую таблицу, выполнив следующую команду Transact-SQL в базе данных **AdventureWorks**:  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  Добавьте новый компонент скрипта в область конструктора потока данных и настройте его в качестве назначения.  
  
4.  Соедините выход источника или преобразования, расположенного выше в потоке данных, с компонентом назначения в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]. (Можно соединить источник непосредственно с назначением, не выполняя никаких преобразований.) Чтобы обеспечить работу этого образца, нужно включить в выход вышестоящего компонента, по меньшей мере, столбцы **AddressID** и **City** из таблицы **Person.Address** образца базы данных **AdventureWorks**.  
  
5.  Откройте **редактор преобразования "Скрипт"** . На странице **Входные столбцы** выберите столбцы **AddressID** и **City**.  
  
6.  На странице **Входы и выходы** измените имя входа на более описательное, например **ВходАдреса**.  
  
7.  На странице **Диспетчеры соединений** добавьте или создайте диспетчер подключений ODBC с описательным именем, например **ДиспетчерПодключенийODBC**.  
  
8.  На странице **Скрипт** нажмите кнопку **изменить скрипт**, а затем введите скрипт, показанный ниже в `ScriptMain` классе.  
  
9. Закройте среду разработки скриптов и **редактор преобразования "Скрипт"** , затем выполните образец.  
  
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
  
![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание назначения с помощью компонента скрипта](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
