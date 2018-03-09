---
title: "MSSQLSERVER_1203 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 1203 (Database Engine error)
ms.assetid: 33a35f00-98c8-46c6-b432-544b326b6117
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67be895813ef4007a83e4e8388d70b15066922e6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver1203"></a>MSSQLSERVER_1203
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1203|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|LK_NOT|  
|Текст сообщения|Идентификатор процесса %d попытался разблокировать ресурс, владельцем которого он не является: %.*ls. Повторите транзакцию, поскольку эта ошибка может быть вызвана фактором времени. Если проблема остается, обратитесь к администратору баз данных.|  
  
## <a name="explanation"></a>Объяснение  
Эта ошибка происходит, когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вовлечен в некоторую деятельность, отличную от обычной завершающей очистки, и при попытке разблокировать определенную страницу обнаруживает, что она уже разблокирована.  
  
### <a name="possible-causes"></a>Возможные причины  
Причина этой ошибки может быть связана с некоторыми структурными проблемами в этой базе данных. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] управляет блокировкой и освобождением страниц, чтобы обеспечить контроль параллелизма в многопользовательской среде. Этот механизм работает за счет использования различных структур внутренней блокировки, идентифицирующих страницу и тип установленной для нее блокировки. Блокировки устанавливаются для обработки определенных страниц и сбрасываются после завершения обработки.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните инструкцию DBCC CHECKDB для базы данных, которой принадлежит объект. Если выполнение DBCC CHECKDB завершится без ошибок, попробуйте заново установить соединение и выполнить команду.  
  
> [!IMPORTANT]  
> Если выполнение DBCC CHECKDB с одним из предложений REPAIR не позволяет устранить неполадку с индексом, или если вы не уверены, как повлияет на данные выполнение инструкции DBCC CHECKDB с предложением REPAIR, обратитесь к основному поставщику услуг по технической поддержке.  
  
