---
title: MSSQLSERVER_17887 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53c67b1050c33addce50755f91218bd8a74e0641
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver17887"></a>MSSQLSERVER_17887
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17887|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Текст сообщения|Прослушиватель завершения операций ввода-вывода (0x%lx) исполнитель 0x%p, по-видимому, не возвращает управление узлу %ld. Примерная загрузка ЦП: ядро %I64d мс, пользователь %I64d мс, интервал: %I64d.|  
  
## <a name="explanation"></a>Объяснение  
Указывает на возможную проблему прослушивателя порта завершения операций ввода-вывода на указанном узле при выполнении подпрограммы завершения ввода-вывода для сетевого события чтения или записи. Эта ошибка исчезнет, когда прослушиватель порта завершения операций ввода-вывода на указанном узле вернет управление после выполнения подпрограммы завершения ввода-вывода.  
  
## <a name="user-action"></a>Действие пользователя  
Обратитесь в службу поддержки пользователей Майкрософт.  
  
