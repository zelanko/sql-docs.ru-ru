---
title: "MSSQL_ENG018456 | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 03184d93644598527b76f054051c66f92ecc6d3e
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng018456"></a>MSSQL_ENG018456
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|18456|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Ошибка входа пользователя '%.*ls'.%.\*ls|  
  
## <a name="explanation"></a>Объяснение  
 Ошибка MSSQL_ENG018456 возникает при неудачной попытке входа в систему. Если сообщение об ошибке включает учетную запись **distributor_admin** (Ошибка входа пользователя 'distributor_admin'.), проблема заключается в учетной записи, которая используется репликацией. Репликация создает удаленный сервер **repl_distributor**, предоставляющий возможность обмена данными между распространителем и издателем. Имя входа **distributor_admin** связано с этим удаленным сервером и должно иметь правильный пароль.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь в том, что для учетной записи указан пароль. Дополнительные сведения см. в разделе [Организация безопасности распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

