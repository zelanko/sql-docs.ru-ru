---
title: Основные классы объектов AMO | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: amo
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b7efa520db59a104452b8bcd799808e7a27a35d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34022791"
---
# <a name="amo-fundamental-classes"></a>Основные классы объектов AMO
  Основу работы с объектами AMO составляют основные классы. Они формируют среду для всех остальных объектов, которые будут использованы в приложении. К фундаментальным классам относятся следующие объекты: <xref:Microsoft.AnalysisServices.Server>, <xref:Microsoft.AnalysisServices.Database>, <xref:Microsoft.AnalysisServices.DataSource>, и <xref:Microsoft.AnalysisServices.DataSourceView>.  
  
 На следующем рисунке показана связь между классами, описываемыми в этом разделе.  
  
 ![Основные классы объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/media/amo-fundamentalclasses.gif "основные классы объектов AMO")  
  
 Этот раздел состоит из следующих подразделов.  
  
-   [Объекты сервера](#ServerObjects)  
  
-   [Объекты базы данных](#DatabaseObjects)  
  
-   [Объекты DataSource и DataSourceView](#DSandDSV)  
  
##  <a name="ServerObjects"></a> Объекты сервера  
 Кроме того, будут доступны следующие методы.  
  
-   Управление соединениями: подключение, Disconnect, Reconnect и GetConnectionState.  
  
-   Управление транзакциями: BeginTransaction, CommitTransaction и RollbackTransaction.  
  
-   Резервное копирование и восстановление.  
  
-   Выполнение DDL: выполнение CancelCommand SendXmlaRequest, StartXmlaRequest.  
  
-   Управление метаданными: UpdateObjects и Validate.  
  
 Для соединения с сервером необходима стандартная строка соединения такая же, как в ADOMD.NET и OLEDB. Дополнительные сведения см. в разделе <xref:System.Configuration.ConnectionStringSettings.ConnectionString%2A>. В качестве строки соединения может быть указано просто имя сервера.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Server> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DatabaseObjects"></a> Объекты базы данных  
 Для работы в приложении с объектом <xref:Microsoft.AnalysisServices.Database> необходимо получить экземпляр базы данных из коллекции баз данных родительского сервера. Для создания базы данных объект <xref:Microsoft.AnalysisServices.Database> необходимо добавить в коллекцию баз данных сервера и обновить новый экземпляр на сервере. Чтобы удалить базу данных, объект <xref:Microsoft.AnalysisServices.Database> удаляют его же методом Drop.  
  
 Создать резервную копию базы данных можно при помощи метода BackUp (объекта <xref:Microsoft.AnalysisServices.Database> или объекта <xref:Microsoft.AnalysisServices.Server>), однако ее восстановление возможно только методом Restore объекта <xref:Microsoft.AnalysisServices.Server>.  
  
 Дополнительные сведения о доступных методах и свойствах см. в описании класса <xref:Microsoft.AnalysisServices.Database> из пространства имен <xref:Microsoft.AnalysisServices>.  
  
##  <a name="DSandDSV"></a> Объекты DataSource и DataSourceView  
 Управление источниками данных обеспечивает объект <xref:Microsoft.AnalysisServices.DataSourceCollection> из класса базы данных. Экземпляр объекта <xref:Microsoft.AnalysisServices.DataSource> можно создать методом Add объекта <xref:Microsoft.AnalysisServices.DataSourceCollection>. Экземпляр объекта <xref:Microsoft.AnalysisServices.DataSource> можно удалить методом Remove объекта <xref:Microsoft.AnalysisServices.DataSourceCollection>.  
  
 Управление объектами <xref:Microsoft.AnalysisServices.DataSourceView> производится из объекта <xref:Microsoft.AnalysisServices.DataSourceViewCollection> класса базы данных.  
  
 Дополнительные сведения о доступных методах и свойствах см. в разделах <xref:Microsoft.AnalysisServices.DataSource> и <xref:Microsoft.AnalysisServices.DataSourceView> в <xref:Microsoft.AnalysisServices>.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices>   
 [Знакомство с классами объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/amo-classes-introduction.md)   
 [Программирование фундаментальных объектов AMO](../../../analysis-services/multidimensional-models/analysis-management-objects/programming-amo-fundamental-objects.md)  
  
  
