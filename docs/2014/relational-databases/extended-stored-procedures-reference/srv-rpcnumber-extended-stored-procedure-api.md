---
title: srv_rpcnumber (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- srv_rpcnumber
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcnumber
ms.assetid: 3094085e-fe9e-423d-bf87-7852352c2d26
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6cffd7bb2a6894632c0d9c9dbf7b825a7bf6d837
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189514"
---
# <a name="srvrpcnumber-extended-stored-procedure-api"></a>srv_rpcnumber (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает компонент номера для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_rpcnumber ( SRV_PROC *  
srvproc   
)  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
## <a name="returns"></a>Возвращает  
 Компонент номера для текущей удаленной хранимой процедуры. Если клиент при выполнении удаленной хранимой процедуры не использует компонент номера (либо при отсутствии текущей удаленной хранимой процедуры), возвращается значение -1.  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает только компонент номера удаленной хранимой процедуры. Она не включает необязательные описатели для владельца, имени удаленной хранимой процедуры и имени базы данных.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  