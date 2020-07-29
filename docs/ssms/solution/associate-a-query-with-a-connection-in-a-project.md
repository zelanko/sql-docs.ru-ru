---
title: Связь запроса с соединением в проекте
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server Management Studio], query associations
- projects [SQL Server Management Studio], connections
- projects [SQL Server Management Studio], query connections
- query associations [SQL Server Management Studio]
ms.assetid: c9625ae0-29c1-4179-a709-51b7e2f9e23d
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 33607941be3289124c216dc5e62a0e4ee790bc35
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003294"
---
# <a name="associate-a-query-with-a-connection-in-a-project"></a>Связь запроса с соединением в проекте
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Если запрос был создан без соединения или если запрос был перемещен из одного проекта в другой, он не будет связан с соединением в текущем проекте.  
  
### <a name="to-associate-a-query-with-a-connection-in-a-project"></a>Связывание запроса с соединением в проекте  
  
1.  Если запрос открыт в редакторе запросов, щелкните правой кнопкой мыши в пустой области редактора запросов и в контекстном меню укажите **Соединение**, а затем **Соединить**. Если запрос не открыт, для соединения запроса дважды щелкните запрос в обозревателе решений.  
  
2.  В диалоговом окне **Подключиться к ядру СУБД** введите сведения о соединении. Если они совпадут с существующим соединением, запрос будет связан с этим соединением.  
  
## <a name="see-also"></a>См. также:  
[Обозреватель решений](../../ssms/solution/solution-explorer.md)  
[Изменение соединения, связанного с запросом](../../ssms/solution/change-the-connection-associated-with-a-query.md)  
[Просмотр или изменение свойств соединения в проекте](../../ssms/solution/view-or-change-the-properties-of-a-connection-in-a-project.md)  
  
