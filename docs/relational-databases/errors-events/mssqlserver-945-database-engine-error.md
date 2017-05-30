---
title: "MSSQLSERVER_945 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
caps.latest.revision: 20
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 49eb8e4472666be24a7edd1549dfe0e3705fd939
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver945"></a>MSSQLSERVER_945
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|945|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_IS_SHUTDOWN|  
|Текст сообщения|Не удалось открыть базу данных «%.*ls» вследствие недоступности файлов, нехватки памяти или места на диске.  Подробности см. в журнале ошибок SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось обратиться к базе данных из-за отсутствия файлов или других ресурсов.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, нет ли в журнале ошибок дополнительных сведений об ошибках памяти, места на диске или разрешений. Проверьте местоположение MDF- и NDF-файлов этой базы данных и удостоверьтесь, что у учетной записи, используемой компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], есть разрешения на доступ к этим файлам. После устранения неполадки перезапустите базу данных, установив параметр ONLINE в инструкции ALTER DATABASE.  
  

