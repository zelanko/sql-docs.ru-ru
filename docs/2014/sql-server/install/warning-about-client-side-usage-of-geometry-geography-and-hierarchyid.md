---
title: Предупреждение об использовании геометрии, GEOGRAPHY и HIERARCHYID на стороне клиента | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 524400e9c9420fb54447220215d4660874ec6d69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091091"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Предупреждение об использовании GEOMETRY, GEOGRAPHY и HIERARCHYID на стороне клиента
  Сборка **Microsoft. SqlServer. types. dll**, которая содержит типы пространственных данных, обновлена с версии 10,0 до версии 11,0. Пользовательские приложения, ссылающиеся на эту сборку, могут завершаться с ошибками, если выполняются определенные условия.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Сборка **Microsoft. SqlServer. types. dll**, которая содержит типы пространственных данных, обновлена с версии 10,0 до версии 11,0. Пользовательские приложения, ссылающиеся на эту сборку, могут завершаться с ошибками, если выполняются следующие условия.  
  
-   При перемещении пользовательского приложения с компьютера, на [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] котором установлено приложение, на компьютер, на котором установлено [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] только приложение, произойдет сбой приложения из-за отсутствия ссылки на версию 10,0 для сборки **sqltypes** . Может отображаться следующее сообщение об ошибке: `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Если также установлена ссылка на сборку **sqltypes** версии 11,0 и версия 10,0, может появиться следующее сообщение об ошибке:`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   При ссылке на сборку **sqltypes** версии 11,0 из пользовательского приложения, предназначенного для .NET 3,5, 4 или 4,5, происходит сбой приложения, так как SqlClient по проектированию загружает версию 10,0 сборки. Эта ошибка возникает, когда приложение вызывает один из следующих методов:  
  
    -   Метод `GetValue` класса `SqlDataReader`.  
  
    -   Метод `GetValues` класса `SqlDataReader`.  
  
    -   индексный оператор квадратных скобок [] из класса `SqlDataReader`  
  
    -   Метод `ExecuteScalar` класса `SqlCommand`.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Для разрешения этой проблемы можно воспользоваться одним из следующих методов:  
  
-   Для разрешения этой проблемы в коде можно вызвать метод `GetSqlBytes` вместо перечисленных выше методов Get для получения системных типов CLR [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], как показано в следующем примере.  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   Для разрешения этой проблемы можно воспользоваться перенаправлением сборок в файле конфигурации, как показано в следующем примере.  
  
    ```xml  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    ```  
  
-   Для разрешения этой проблемы в строке подключения можно указать значение «SQL Server 2012» для атрибута «Type System Version», что обеспечивает в SqlClient принудительную загрузку версии 11.0 сборки. Этот атрибут строки подключения доступен только в платформе .NET 4.5 и выше.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md
)  
  
  
