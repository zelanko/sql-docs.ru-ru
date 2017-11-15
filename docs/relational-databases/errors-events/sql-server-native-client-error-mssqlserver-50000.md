---
title: "MSSQLSERVER_50000 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 50000 [SQL Server Native Client setup error]
ms.assetid: 5426d87a-d5d9-4984-b211-b07d69e834a2
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 84f6e861c63326b2fd972d987bb45fa56635fd0f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="sql-server-native-client-error-mssqlserver50000"></a>Ошибки собственного клиента SQL Server MSSQLSERVER_50000
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Номер версии продукта|11.0|  
|Идентификатор события|50000|  
|Источник события|SETUP|  
|Компонент|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственный клиент|  
|Символическое имя||  
|Текст сообщения|Произошла сетевая ошибка при попытке чтения из файла «%.*ls».|  
  
## <a name="explanation"></a>Объяснение  
 Была сделана попытка установить (или обновить) собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на компьютер, где собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] уже установлен и где существующая установка производилась из MSI-файла, который был переименован из sqlncli.msi.  
  
## <a name="user-action"></a>Действие пользователя  
 Для разрешения этой ошибки удалите существующую версию собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы предотвратить эту ошибку, не устанавливайте собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из MSI-файла, который не называется sqlncli.msi.  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
