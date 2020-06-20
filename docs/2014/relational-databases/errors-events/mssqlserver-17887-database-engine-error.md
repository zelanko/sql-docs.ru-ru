---
title: MSSQLSERVER_17887 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 006e616d80ef7e8d083f60675b02b4e6a4e8dc24
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84967754"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17887|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Текст сообщения|Прослушиватель завершения операций ввода-вывода (0x%lx) исполнитель 0x%p, по-видимому, не возвращает управление узлу %ld. Примерная загрузка ЦП: ядро %I64d мс, пользователь %I64d мс, интервал: %I64d.|  
  
## <a name="explanation"></a>Объяснение  
 Указывает на возможную проблему прослушивателя порта завершения операций ввода-вывода на указанном узле при выполнении подпрограммы завершения ввода-вывода для сетевого события чтения или записи. Эта ошибка исчезнет, когда прослушиватель порта завершения операций ввода-вывода на указанном узле вернет управление после выполнения подпрограммы завершения ввода-вывода.  
  
## <a name="user-action"></a>Действие пользователя  
 Обратитесь в службу поддержки пользователей Майкрософт.  
  
  
