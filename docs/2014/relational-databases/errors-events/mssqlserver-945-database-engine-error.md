---
title: MSSQLSERVER_945 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 945 (Database Engine error)
ms.assetid: ee501d13-0bd9-4627-896c-ed5b1bdb88b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 913778fc4c40a76cb3a7f5aca07b981567428253
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553069"
---
# <a name="mssqlserver_945"></a>MSSQLSERVER_945
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
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
  
  
