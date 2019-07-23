---
title: MSSQLSERVER_17128 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17128 (Database Engine error)
ms.assetid: 7b15a5e6-fd41-47ce-ba87-54f72acea4bb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 210df5d533908e75e83b348ac6c9a84a22198f4b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68131816"
---
# <a name="mssqlserver17128"></a>MSSQLSERVER_17128
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17128|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NOBUFSPACE|  
|Текст сообщения|initdata: недостаточно памяти для буферов ядра.|  
  
## <a name="explanation"></a>Объяснение  
Не удается провести начальное выделение памяти из буферного пула или резервирование памяти. SQL Server завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
Эта обычно случается при запуске SQL Server на очень маломощном компьютере, параметры которого не достигают минимальных требований к системе.  
  
