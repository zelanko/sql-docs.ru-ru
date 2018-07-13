---
title: MSSQLSERVER_26014 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b018c28ec8f718d74d00aec1cdb6fa74b9140118
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411043"
---
# <a name="mssqlserver26014"></a>MSSQLSERVER_26014
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|26014|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SNI_SSL_USER_CERT_FAILURE|  
|Текст сообщения|Не удалось загрузить указанный пользователем сертификат [Cert Hash(sha1) "%hs"]. Сервер не будет принимать соединения. Убедитесь в том, что сертификат установлен правильно. См. раздел «Настройка сертификата для использования протоколом SSL» в электронной документации.|  
  
## <a name="explanation"></a>Объяснение  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] попытался загрузить сертификат, указанный в сообщении, но эта операция окончилась неудачей. Необходимо устранить эту проблему, прежде чем использовать этот сертификат в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Возможны следующие причины ошибки.  
  
-   Сертификат перемещен или удален.  
  
-   Изменилось имя входа, используемое в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не имеет разрешения для доступа к сертификату.  
  
-   Истек срок действия сертификата.  
  
## <a name="user-action"></a>Действие пользователя  
 Убедитесь, что сертификат, указанный в сообщении, существует в системе, является доступным и допустимым для использования.  
  
  
