---
title: "Диалоговое окно \"Параметры запроса\" (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdtsql.chm:69645
- vdt.dlgbox.definequeryparameters
ms.assetid: 31cdaee2-d7cd-4d64-a45f-924b27e8b1f0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: fbf5a6857226aee3b091aa63ac8fe7868c55c68d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/18/2017

---
# <a name="query-parameters-dialog-box-visual-database-tools"></a>Диалоговое окно «Параметры запроса» (визуальные инструменты для баз данных)
Данное диалоговое окно позволяет вводить значения для параметров, определенных в запросе. Это диалоговое окно появляется при выполнении запроса, содержащего параметры, которые должны быть введены конечным пользователем во время запуска.  
  
## <a name="options"></a>Параметры  
**Название**  
Список параметров, определенных для выполняемого запроса. Если запрос содержит именованные параметры, то имена отобразятся в списке. Если запрос содержит неименованные параметры, то для каждого параметра запроса в списке будут приведены имена параметров, определенные системой.  
  
**Значение**  
Введите значение для каждого параметра, приведенного в списке **Имя**. Значение, использованное в последний раз, будет отображено в качестве значения параметра по умолчанию.  
  
## <a name="example"></a>Пример  
Следующий запрос на панели SQL открывает диалоговое окно «Параметры запроса» при выполнении в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject_md.md)] .  
  
```  
SELECT   FirstName, LastName  
FROM    Person.Person AS Lastname  
WHERE   (LastName = @Param1);  
```  
  
## <a name="see-also"></a>См. также:  
[Запрос с параметрами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
  

