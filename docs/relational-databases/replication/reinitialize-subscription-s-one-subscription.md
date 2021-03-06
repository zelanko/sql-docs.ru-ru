---
description: Повторная инициализация подписок — одна подписка
title: Повторная инициализация подписок — одна подписка | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.reinit.single.f1
helpviewer_keywords:
- Reinitialize Subscription(s) dialog box
ms.assetid: 9b0cf0be-d1f1-4163-a0ca-d6f095aa707e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 3cf45a2b5388b8ad35b2cb25fa94581709da71f7
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468835"
---
# <a name="reinitialize-subscriptions---one-subscription"></a>Повторная инициализация подписок — одна подписка
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  При помощи диалогового окна **Повторная инициализация подписок** можно выбрать подписки для повторной инициализации. Повторная инициализация подразумевает применение моментального снимка к подписчику; она выполняется агентом распространителя для подписок на публикации транзакций и агентом слияния для подписок на публикации слиянием.  
  
## <a name="options"></a>Варианты  
 **Использовать текущий моментальный снимок**  
 Выберите, чтобы применить текущий моментальный снимок к подписчику при следующем запуске агента распространителя или агента слияния. Если допустимый моментальный снимок отсутствует, этот параметр выбрать нельзя.  
  
 **Использовать новый моментальный снимок**  
 Выберите, чтобы выполнить повторную инициализацию подписки с новым моментальным снимком. Этот моментальный снимок можно применять к подписчику только после того, как он был сформирован агентом моментальных снимков. Если агент моментальных снимков запускается по расписанию, подписка не будет повторно инициализирована до следующего запланированного запуска агента моментальных снимков.  
  
 Выберите **Создать новый моментальный снимок** для немедленного запуска агента моментальных снимков.  
  
 **Передать несинхронизированные изменения перед повторной инициализацией**  
 Только репликация слиянием. Выберите, чтобы передать все ожидающие обработки изменения из базы данных подписки, прежде чем данные подписчика будут перезаписаны моментальным снимком.  
  
 Если добавить, удалить или изменить параметризованный фильтр, ожидающие обработки изменения подписчика нельзя будет передать издателю во время повторной инициализации. Если нужно передать изменения, ожидающие обработки, то перед изменением фильтра необходимо синхронизировать все подписки.  
  
 **Пометить для повторной инициализации**  
 Щелкните, чтобы отметить подписку для повторной инициализации. После того как будет доступен моментальный снимок, при следующем запуске для подписки агента распространителя или агента слияния он применяется к подписчику.  
  
## <a name="see-also"></a>См. также  
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)  
  
  
