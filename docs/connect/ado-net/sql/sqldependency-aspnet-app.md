---
title: SqlDependency в приложении ASP.NET
description: Демонстрирует использование уведомлений о запросах из приложения ASP.NET.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 2115d087d837118b99ee3ffded9cae0003b6d4e0
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451961"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency в приложении ASP.NET

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

В примере в этом разделе показано, как использовать <xref:Microsoft.Data.SqlClient.SqlDependency> косвенно, используя объект <xref:System.Web.Caching.SqlCacheDependency> ASP.NET. Объект <xref:System.Web.Caching.SqlCacheDependency> использует <xref:Microsoft.Data.SqlClient.SqlDependency> для прослушивания уведомлений и корректного обновления кэша.  
  
> [!NOTE]
>  В примере кода предполагается, что вы включили уведомления о запросах, выполняя скрипты, [включив уведомления о запросах](enable-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Сведения о примере приложения  
В примере приложения используется одна веб-страница ASP.NET для вывода сведений о продуктах из базы данных **AdventureWorks** SQL Server в элемент управления <xref:System.Web.UI.WebControls.GridView>. При загрузке страницы код записывает текущее время в элемент управления <xref:System.Web.UI.WebControls.Label>. Затем он определяет объект <xref:System.Web.Caching.SqlCacheDependency> и задает свойства объекта <xref:System.Web.Caching.Cache> для хранения данных кэша до трех минут. Затем код подключается к базе данных и получает данные. При загрузке страницы и выполнении приложением ASP.NET будет получать данные из кэша, которые можно проверить, отметив, что время на странице не меняется. Если наблюдаемые данные изменяются, ASP.NET делает недействительным кэш и повторно заполняет элемент управления `GridView` новыми данными, обновляя время, отображаемое в элементе управления `Label`.  
  
## <a name="creating-the-sample-application"></a>Создание примера приложения  
Чтобы создать и запустить пример приложения, выполните следующие действия.  
  
1. Создание нового веб-сайта ASP.NET.  
  
2. Добавьте <xref:System.Web.UI.WebControls.Label> и элемент управления <xref:System.Web.UI.WebControls.GridView> на страницу Default. aspx.  
  
3. Откройте модуль класса страницы и добавьте следующие директивы:  
  
    ```csharp  
    using Microsoft.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Добавьте следующий код в событие `Page_Load` страницы:  
  
    [!code-csharp[DataWorks SqlDependency_Start#1](~/../sqlclient/doc/samples/SqlDependency_Start.cs#1)]
  
5. Добавьте два вспомогательных метода, `GetConnectionString` и `GetSQL`. В определенной строке соединения используются интегрированные средства безопасности. Необходимо будет убедиться, что используемая учетная запись обладает необходимыми разрешениями для базы данных, а в образце базы данных **AdventureWorks** включены уведомления.
  
    [!code-csharp[DataWorks SqlDependency_Start#2](~/../sqlclient/doc/samples/SqlDependency_Start.cs#2)]
  
### <a name="testing-the-application"></a>Тестирование приложения  
Приложение кэширует данные, отображаемые в веб-форме, и обновляет их каждые три минуты, если нет действий. Если в базу данных происходит изменение, кэш обновляется немедленно. Запустите приложение из Visual Studio, которое загружает страницу в браузер. Отображается время обновления кэша, указывающее, когда был обновлен кэш. Подождите три минуты, а затем обновите страницу, в результате чего произойдет событие обратной передачи. Обратите внимание, что время, отображаемое на странице, изменилось. Если обновить страницу менее чем за три минуты, время, отображаемое на странице, останется прежним.  
  
Теперь обновите данные в базе данных, используя команду Transact-SQL UPDATE, и обновите страницу. Отображаемое время теперь указывает, что кэш был обновлен с учетом новых данных из базы данных. Обратите внимание, что хотя кэш обновляется, время, отображаемое на странице, не изменяется, пока не произойдет событие обратной передачи.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
