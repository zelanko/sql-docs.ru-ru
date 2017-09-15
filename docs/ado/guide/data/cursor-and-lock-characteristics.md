---
title: "Курсор и характеристиками блокировок | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locks [ADO], characteristics
- adOpenDynamic [ADO]
- cursors [ADO], characteristics
ms.assetid: 459c29cb-4230-42bf-8cc2-f3132ccc7aba
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a1313c42582efee8330abb89a03645dc1491217
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="cursor-and-lock-characteristics"></a>Курсор и характеристиками блокировок
Во время характеристики курсора зависит от возможностей поставщика, достоинства и недостатки обычно применяются для различных типов курсоров и блокировок.  
  
|Тип курсора или блокировки|Преимущества|Недостатки|  
|-------------------------|----------------|-------------------|  
|**adOpenForwardOnly**|-Требования к нехватки ресурсов|-Не может быть прокручен назад<br />-Нет данных параллелизма|  
|**adOpenStatic**|-Прокрутки|-Нет данных параллелизма|  
|**adOpenKeyset**|-Некоторые данных параллелизма<br />-Прокрутки|-Выше требований к ресурсам<br />-Не доступно в сценарии отсоединения|  
|**adOpenDynamic**|-Concurrency данных<br />-Прокрутки|— Наибольшее требования к ресурсам<br />-Не доступно в сценарии отсоединения|  
|**adLockReadOnly**|-Требования к нехватки ресурсов<br />-Высокомасштабируемых|-Данные, не обновить через курсор|  
|**adLockBatchOptimistic**|-Пакетных обновлений<br />-Позволяет без подключения к сети<br />-Другим пользователям доступ к данным|-Данные могут быть изменены несколькими пользователями одновременно|  
|**adLockPessimistic**|-Данные не могут быть изменены другим пользователям при блокировке|-Запрещает другим пользователям доступа к данным в заблокированном состоянии|  
|**adLockOptimistic**|-Другим пользователям доступ к данным|-Данные могут быть изменены несколькими пользователями одновременно|
