---
title: Предупреждение об использовании GEOMETRY, GEOGRAPHY и HIERARCHYID стороны клиента | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 500ee6b3-2154-45d2-a3cf-8760166d9413
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 02748f9dca8e4f9f29c7c94658d2a4068b1ba65e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193722"
---
# <a name="warning-about-client-side-usage-of-geometry-geography-and-hierarchyid"></a>Предупреждение об использовании GEOMETRY, GEOGRAPHY и HIERARCHYID на стороне клиента
  Сборка **Microsoft.SqlServer.Types.dll**, который содержит Пространственные типы данных, была обновлена с версии 10.0 до версии 11.0. Пользовательские приложения, ссылающиеся на эту сборку, могут завершаться с ошибками, если выполняются определенные условия.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Сборка **Microsoft.SqlServer.Types.dll**, который содержит Пространственные типы данных, была обновлена с версии 10.0 до версии 11.0. Пользовательские приложения, ссылающиеся на эту сборку, могут завершаться с ошибками, если выполняются следующие условия.  
  
-   При перемещении пользовательского приложения с компьютера, на котором [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] была установлена на компьютере, на котором только [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] — установлен, приложение завершится сбоем, поскольку указанная в ссылке версия 10.0 из **SqlTypes** сборки не указан. Может отображаться следующее сообщение об ошибке: `“Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified.”`  
  
-   При создании ссылки **SqlTypes** сборки версии 11.0, а также установленной версии 10.0, может появиться следующее сообщение об ошибке: `“System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'.”`  
  
-   При создании ссылки **SqlTypes** сборки версии 11.0 из пользовательского приложения, ориентированном на .NET 3.5, 4 или 4.5, приложение завершится сбоем, поскольку SqlClient изначально загружает версию сборки 10.0. Эта ошибка возникает, когда приложение вызывает один из следующих методов:  
  
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
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
