---
title: SqlDependency в приложении ASP.NET
description: Демонстрирует использование уведомлений запросов из приложения ASP.NET.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: ff226ce3-f6b5-47a1-8d22-dc78b67e07f5
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daenge
ms.reviewer: v-kaywon
ms.openlocfilehash: 403346644d04839d1b24acd2d90e18226a951d90
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80918680"
---
# <a name="sqldependency-in-an-aspnet-application"></a>SqlDependency в приложении ASP.NET

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В приведенном в этом разделе примере показано, как применять <xref:Microsoft.Data.SqlClient.SqlDependency> косвенно, используя объект <xref:System.Web.Caching.SqlCacheDependency> ASP.NET. Объект <xref:System.Web.Caching.SqlCacheDependency> использует <xref:Microsoft.Data.SqlClient.SqlDependency> для прослушивания уведомлений и корректного обновления кэша.  
  
> [!NOTE]
>  В примере кода предполагается, что уведомления о запросах включены путем выполнения скриптов из [этой статьи](enable-query-notifications.md).  
  
## <a name="about-the-sample-application"></a>Сведения о примере приложения  
В примере приложения используется одна веб-страница ASP.NET для вывода сведений о продуктах из базы данных **AdventureWorks** SQL Server в элемент управления <xref:System.Web.UI.WebControls.GridView>. При загрузке страницы код записывает текущее время в элемент управления <xref:System.Web.UI.WebControls.Label>. Затем он определяет объект <xref:System.Web.Caching.SqlCacheDependency> и задает свойства объекта <xref:System.Web.Caching.Cache> для сохранения данных кэша до трех минут. Затем код подключается к базе данных и получает данные. При загрузке страницы и работе приложения ASP.NET будет получать данные из кэша, которые можно проверить, отметив, что время на странице не меняется. Если наблюдаемые данные изменяются, ASP.NET делает недействительным кэш и повторно заполняет элемент управления `GridView` новыми данными, обновляя время в элементе управления `Label`.  
  
## <a name="creating-the-sample-application"></a>Создание примера приложения  
Чтобы создать и запустить пример приложения, выполните следующие действия:  
  
1. Создание нового веб-сайта ASP.NET.  
  
2. Добавьте <xref:System.Web.UI.WebControls.Label> и элемент управления <xref:System.Web.UI.WebControls.GridView> на страницу Default.aspx.  
  
3. Откройте модуль класса страницы и добавьте следующие директивы:  
  
    ```csharp  
    using Microsoft.Data.SqlClient;  
    using System.Web.Caching;  
    ```  
  
4. Добавьте следующий код в событие `Page_Load` страницы:  
  
    [!code-csharp[DataWorks SqlDependency_Start#1](~/../sqlclient/doc/samples/SqlDependency_Start.cs#1)]
  
5. Добавьте два вспомогательных метода: `GetConnectionString` и `GetSQL`. В определенной строке соединения используются интегрированные средства безопасности. Необходимо будет убедиться, что используемая учетная запись обладает необходимыми разрешениями для базы данных, а в образце базы данных **AdventureWorks** включены уведомления.
  
    [!code-csharp[DataWorks SqlDependency_Start#2](~/../sqlclient/doc/samples/SqlDependency_Start.cs#2)]
  
### <a name="testing-the-application"></a>Тестирование приложения  
Приложение кэширует данные, отображаемые в веб-форме, и обновляет их каждые три минуты, если нет действий. Если в базе данных происходит изменение, кэш обновляется немедленно. Запустите приложение из Visual Studio, чтобы загрузить страницу в браузер. Отображаемое время обновления кэша указывает, когда кэш был обновлен последний раз. Подождите три минуты, а затем обновите страницу, в результате чего произойдет событие обратной передачи. Обратите внимание, что время, отображаемое на странице, изменилось. Если обновить страницу меньше чем через три минуты, время, отображаемое на странице, останется прежним.  
  
Теперь обновите данные в базе данных, используя команду Transact-SQL UPDATE, и обновите страницу. Отображаемое время теперь указывает, что кэш был обновлен с учетом новых данных из базы данных. Обратите внимание, что хотя кэш обновляется, время на странице не изменяется, пока не произойдет событие обратной передачи.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [Уведомления запросов в SQL Server](query-notifications-sql-server.md)
