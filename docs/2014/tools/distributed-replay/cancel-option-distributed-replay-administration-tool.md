---
title: Параметр отмены (средство администрирования распределенного воспроизведения) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: fea376de-307a-4b45-b7e2-37df88f3681a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ce29f56d7877712dd99553968b364b1c33471c2b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177334"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Параметр отмены (средство администрирования распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Средство `DReplay.exe`администрирования распределенное воспроизведение — это средство командной строки, которое можно использовать для взаимодействия с контроллером распределенного воспроизведения. В этом разделе описывается параметр командной строки **cancel** и соответствующий синтаксис.

 Параметр **cancel** отменяет текущую операцию, выполняемую на контроллере.

 ![Значок ссылки на раздел](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Синтаксис

```

dreplay cancel [-mcontroller] [-q] 
```

#### <a name="parameters"></a>Параметры
 **-m** *контроллер* имя компьютера контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».

 Если параметр **-m** не задан, то используется локальный компьютер.

 **-q** Тихий режим. Не запрашивает подтверждения.

 Параметр **-q** необязателен.

## <a name="examples"></a>Примеры
 В следующем примере запрос отмены передается в тихом режиме. Значение `localhost` указывает, что служба контроллера запущена на том же компьютере, что и средство администрирования.

```
dreplay cancel -m localhost -q
```

## <a name="permissions"></a>Разрешения
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.

 Дополнительные сведения см. в статье [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>См. также:
 [Распределенное воспроизведение SQL Server](sql-server-distributed-replay.md)


