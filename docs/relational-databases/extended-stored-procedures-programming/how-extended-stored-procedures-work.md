---
title: Принципы работы расширенных хранимых процедур | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: extended-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], about extended stored procedures
ms.assetid: 6e946d8c-3268-4b59-8a1c-1637909cd701
caps.latest.revision: 33
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: bd0996750aff15fc94a17b669092552a021bf34b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32935109"
---
# <a name="how-extended-stored-procedures-work"></a>Принципы работы расширенных хранимых процедур
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Принцип работы расширенной хранимой процедуры заключается в следующем.  
  
1.  Когда клиент выполняет расширенную хранимую процедуру, запрос передается в поток табличных данных (TDS) или формате Simple Object Access Protocol (SOAP) из клиентского приложения для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
2.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ищет DLL-библиотеки, связанные с расширенной хранимой процедурой, и загружает их, если они еще не загружены.  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает запрошенную расширенную хранимую процедуру (реализованную как функцию внутри DLL-библиотеки).  
  
4.  Расширенная хранимая процедура передает результирующий набор и возвращает параметры обратно на сервер через API-интерфейс расширенной хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Программирование расширенных хранимых процедур ядра СУБД](../../relational-databases/database-engine-extended-stored-procedure-programming.md)  
  
  
