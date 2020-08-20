---
description: Ошибка ядра СУБД MSSQLSERVER_802
title: Ошибка ядра СУБД MSSQLSERVER_802 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 802 (Database Engine error)
ms.assetid: 5892ed24-4dcb-4bf9-a8a4-a7ca898832d5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c6beb0d2b1930f03955918e1464d2a7eb966db66
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482738"
---
# <a name="mssqlserver_802---database-engine-error"></a>Ошибка ядра СУБД MSSQLSERVER_802
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|802|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NO_BUFS|  
|Текст сообщения|Недостаточно свободной памяти в буферном пуле.|  
  
## <a name="explanation"></a>Объяснение  
Это происходит, если буферный пул заполнен и не может больше увеличиваться.  
  
## <a name="user-action"></a>Действие пользователя  
Далее представлены общие шаги, которые помогут при устранении неполадок с памятью.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Buffer Manager**, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **: Memory Manager**.  
  
3.  Проверьте следующие параметры конфигурации памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
    Обратите внимание на любые необычные параметры и исправьте их при необходимости. Принимайте во внимание тот факт, что в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предъявляются повышенные требования к доступному объему памяти. Настройки по умолчанию приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в разделе «Настройка параметров конфигурации сервера».  
  
4.  Обратите внимание на сообщения инструкции DBCC MEMORYSTATUS и способ их изменения при появлении сообщений об ошибках.  
  
5.  Проверьте рабочую нагрузку (число параллельных сеансов, выполняющихся запросов).  
  
Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если ресурсы потребляют приложения, выполняющиеся вместе с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], попробуйте остановить эти приложения или выполнить их на отдельном сервере.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  
