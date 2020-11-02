---
description: MSSQLSERVER_854
title: MSSQLSERVER_854
ms.custom: ''
ms.date: 08/20/2020
ms.prod: sql
ms.reviewer: ramakoni1, pijocoder, suresh-kandoth, Masha
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 854 (Database Engine error)
ms.assetid: ''
author: suresh-kandoth
ms.author: ramakoni
ms.openlocfilehash: f0bf9061b452329280f0625bcc1339469372f4df
ms.sourcegitcommit: ead0b8c334d487a07e41256ce5d6acafa2d23c9d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92418874"
---
# <a name="mssqlserver_854"></a>MSSQLSERVER_854
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

## <a name="details"></a>Сведения

|attribute|Значение|
|---|---|
|Название продукта|SQL Server|
|Идентификатор события|854|
|Источник события|MSSQLSERVER|
|Компонент|SQLEngine|
|Символическое имя|HARDWARE_MEMORY_SCRUBBER|
|Текст сообщения|Компьютер поддерживает восстановление ошибок памяти. Защита памяти SQL включена и обеспечивает восстановление от сбоев памяти.|
||

## <a name="explanation"></a>Пояснение

Это сообщение означает, что оборудование и операционная система поддерживают возможность восстановления после ошибок памяти. На компьютерах с более новым оборудованием и ОС Windows Server 2012 или более поздней версии оборудование может уведомлять операционную систему и приложения о том, что страницы памяти (страницы операционной системы) помечены как поврежденные. Такие приложения, как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут регистрировать эти уведомления с помощью следующего набора API:

- `GetMemoryErrorHandlingCapabilities`
- `RegisterBadMemoryNotification`
- `BadMemoryCallbackRoutine`

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] добавляет поддержку этих уведомлений в Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2012 и более поздних версиях. Во время запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверяет, поддерживает ли оборудование эту новую функцию. Кроме того, в журнале ошибок появится следующее сообщение:

> \<Datetime> Компьютер сервера поддерживает восстановление ошибок памяти. Защита памяти SQL включена и обеспечивает восстановление от сбоев памяти.

## <a name="user-action"></a>Рекомендуемые действия

Проверьте, возникают ли другие ошибки, например 855 и 856, и выполните соответствующее корректирующее действие.

## <a name="more-information"></a>Дополнительные сведения

Чтобы сервер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не регистрировал уведомления об ошибках памяти в операционной системе, можно использовать флаг трассировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 849. Однако имейте в виду, что включение флага трассировки 849 не позволит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] получать уведомления о повреждениях памяти от операционной системы. Поэтому в обычных обстоятельствах использовать его не рекомендуется.
