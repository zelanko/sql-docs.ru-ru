---
title: "srv_setutype (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_setutype
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_setutype
ms.assetid: 6160f15d-1b68-411e-ab6d-491ec288f264
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 82ad2ec5c5fc400814eaab556d55bbc78b9c6d38
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="srvsetutype-extended-stored-procedure-api"></a>srv_setutype (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Устанавливает определяемый пользователем тип данных для столбца строки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setutype (  
SRV_PROC *  
srvproc  
,  
int   
column  
,   
DBINT  
user_type   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *column*  
 Указывает, какой столбец устанавливать. Нумерация столбцов начинается с 1.  
  
 *user_type*  
 Указывает код определяемого пользователем типа данных.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL. Если столбец не существует, возвращает значение FAIL.  
  
## <a name="remarks"></a>Замечания  
 Столбец имеет два типа данных: фактический и определяемый пользователем. Определяемый пользователем тип данных используется [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для хранения действительного определяемого пользователем типа данных столбца, и сведения об описании столбца, например допустимость значения NULL и возможность обновления (если таковые существуют).  
  
 Функцию **srv_setutype** можно вызвать в любое время после определения *column* с помощью функции **srv_describe** и до передачи последней строки.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_describe (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
