---
title: MSSQLSERVER_17204 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17204 (Database Engine error)
ms.assetid: 40db66f9-dd5e-478c-891e-a06d363a2552
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75eab047579e11812abe1aef15b13dde82dc1fb9
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17204"></a>MSSQLSERVER_17204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17204|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBLKIO_DEVOPENFAILED|  
|Текст сообщения|%ls: Не удалось открыть файл %ls для номера файла %d.  Ошибка операционной системы: %ls.|  
  
## <a name="explanation"></a>Объяснение  
Программе SQL Server не удалось открыть указанный файл из-за указанной ошибки.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину, исправьте ошибку операционной системы, затем еще раз попытайтесь выполнить операцию.  
  
