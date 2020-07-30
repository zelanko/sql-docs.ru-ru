---
title: srv_setcollen (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
description: Узнайте, как srv_setcollen задает текущую длину данных в байтах столбца переменной длины или столбца, допускающего значения NULL.
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e87c0728bf68fb7cae076d25cbda0ac43a7ed3ef
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87332466"
---
# <a name="srv_setcollen-extended-stored-procedure-api"></a>srv_setcollen (API-интерфейс расширенных хранимых процедур)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
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
  
## <a name="returns"></a>Результаты  
 SUCCEED или FAIL.  
  
## <a name="remarks"></a>Remarks  
 Каждый столбец строки должен сначала быть определен с помощью **srv_describe**. Длина данных столбца устанавливается последним вызовом к **srv_describe** или **srv_setcollen**. Если в строке изменяются данные переменной длины (данные, оканчивающиеся нулевым байтом), необходимо использовать **srv_setcollen**, чтобы установить новую длину перед вызовом **srv_sendrow**. Для столбца, в котором разрешены значения NULL, процедура **srv_describe** должна быть вызвана с параметром *desttype*, для которого установлен тип данных, допускающий значения NULL (например, SRVINTN), а данные, которые могут принимать значение NULL, задаются путем вызова процедуры **srv_setcollen** с параметром *len*, установленным в значение 0. Данные с нулевой длиной не могут быть указаны в API-интерфейсе расширенных хранимых процедур.  
  
 Обратите внимание, что если тип данных столбца имеет переменную длину, *len* не проверяется. Если эта функция вызвана для столбца переменной длины, то возвращается значение FAIL.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_describe (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-describe-extended-stored-procedure-api.md)  
  
  
