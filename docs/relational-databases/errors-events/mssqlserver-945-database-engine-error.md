---
title: MSSQLSERVER_945 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5eb5efa87dbc6c94ffe591929460e036eedc6c42
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85636380"
---
# <a name="mssqlserver_945"></a>MSSQLSERVER_945
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|945|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_IS_SHUTDOWN|  
|Текст сообщения|Не удалось открыть базу данных «%.*ls» вследствие недоступности файлов, нехватки памяти или места на диске.  Подробности см. в журнале ошибок SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось обратиться к базе данных из-за отсутствия файлов или других ресурсов.  
  
## <a name="user-action"></a>Действие пользователя  
Проверьте, нет ли в журнале ошибок дополнительных сведений об ошибках памяти, места на диске или разрешений. Проверьте местоположение MDF- и NDF-файлов этой базы данных и удостоверьтесь, что у учетной записи, используемой компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)], есть разрешения на доступ к этим файлам. После устранения неполадки перезапустите базу данных, установив параметр ONLINE в инструкции ALTER DATABASE.  
  
