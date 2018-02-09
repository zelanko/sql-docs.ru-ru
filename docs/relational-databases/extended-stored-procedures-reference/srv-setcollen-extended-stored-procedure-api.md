---
title: "srv_setcollen (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- srv_setcollen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_setcollen
ms.assetid: 3c60f1c3-4562-463a-a259-12df172788bd
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1e6ae488fb188a0243ebca59b69641facafd2ecf
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="srvsetcollen-extended-stored-procedure-api"></a>srv_setcollen (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Указывает текущую длину данных в байтах столбца переменной длины или столбца, допускающего значения NULL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_setcollen (  
SRV_PROC *  
srvproc  
,  
int   
column  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *column*  
 Указывает номер столбца, для которого задана длина данных. Нумерация столбцов начинается с 1.  
  
 *len*  
 Указывает длину столбца данных в байтах. Длина 0 означает, что значение данных столбца — NULL.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Каждый столбец строки должен сначала быть определен с помощью **srv_describe**. Длина данных столбца устанавливается последним вызовом к **srv_describe** или **srv_setcollen**. Если в строке изменяются данные переменной длины (данные, оканчивающиеся нулевым байтом), необходимо использовать **srv_setcollen**, чтобы установить новую длину перед вызовом **srv_sendrow**. Для столбца, в котором разрешены значения NULL, процедура **srv_describe** должна быть вызвана с параметром *desttype*, для которого установлен тип данных, допускающий значения NULL (например, SRVINTN), а данные, которые могут принимать значение NULL, задаются путем вызова процедуры **srv_setcollen** с параметром *len*, установленным в значение 0. Данные с нулевой длиной не могут быть указаны в API-интерфейсе расширенных хранимых процедур.  
  
 Обратите внимание, что если тип данных столбца имеет переменную длину, *len* не проверяется. Если эта функция вызвана для столбца переменной длины, то возвращается значение FAIL.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также  
 [srv_describe (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
