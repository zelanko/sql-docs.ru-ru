---
title: Проверка на наличие проблем с задержками ввода-вывода в подсистеме дискового ввода-вывода | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 86cf15a2e8191171c7b7ca80ae6e78a2fc9fc571
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095920"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a>Проверка на наличие проблем задержки ввода-вывода в подсистеме дискового ввода-вывода
  Это правило проверяет журнал событий на наличие сообщения об ошибке 833. Это сообщение указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издал запрос чтения или записи на диск, и выполнение запроса заняло более 15 секунд. Эта ошибка выдается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указывает на проблему в подсистеме дискового ввода-вывода. Такие долгие задержки могут существенно снизить производительность среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Для устранения этой ошибки найдите в журнале системных событий сообщения об ошибках, связанных с оборудованием. Также изучите журналы оборудования, если они доступны.  
  
 При помощи системного монитора проверьте следующие счетчики.  
  
-   Среднее время обращения к диску (сек)  
  
-   Средняя длина очереди диска  
  
-   Текущая длина очереди диска  
  
 Например, значение Average Disk Sec/Transfer на компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , обычно не превышает 15 миллисекунд. Если значение счетчика Average Disk Sec/Transfer увеличивается, это указывает на то, что подсистема ввода-вывода диска не справляется с запросами на операции ввода-вывода.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [MSSQLSERVER_833](../errors-events/mssqlserver-833-database-engine-error.md)  
  
 [Статья 897284 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117743)  
  
 [Основные операции ввода-вывода в SQL Server, раздел 2](http://go.microsoft.com/fwlink/?LinkId=69370)  
  
  