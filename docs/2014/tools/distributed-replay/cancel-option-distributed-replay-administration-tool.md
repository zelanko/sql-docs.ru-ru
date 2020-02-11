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
ms.openlocfilehash: f6d9aa28d4a6879f3077b137880aae54b9a0c434
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63149878"
---
# <a name="cancel-option-distributed-replay-administration-tool"></a>Параметр отмены (средство администрирования распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Средство `DReplay.exe`администрирования распределенное воспроизведение — это средство командной строки, которое можно использовать для взаимодействия с контроллером распределенного воспроизведения. В этом разделе описывается параметр командной строки **cancel** и соответствующий синтаксис.  
  
 Параметр **cancel** отменяет текущую операцию, выполняемую на контроллере.  
  
 ![Значок ссылки на раздел](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых с синтаксисом средств администрирования, см. в разделе [соглашения о синтаксисе Transact-sql &#40;&#41;Transact-SQL ](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
dreplay cancel [-mcontroller] [-q]   
```  
  
#### <a name="parameters"></a>Параметры  
 *контроллер* **-m**  
 Имя компьютера для контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».  
  
 Если параметр **-m** не задан, то используется локальный компьютер.  
  
 **-q**  
 Тихий режим. Не запрашивает подтверждения.  
  
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
  
  
