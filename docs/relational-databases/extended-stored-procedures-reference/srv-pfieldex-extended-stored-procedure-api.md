---
title: "srv_pfieldex (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/16/2017
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
- srv_pfieldex
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 70f36511846d7435cc940ea65f871c462130958d
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="srvpfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Пользуйтесь вместо этого интеграцией со средой CLR.  
  
 Возвращает указатель на данные, содержащие в запрошенном поле SRV_PROC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, который представляет собой дескриптор соединения с клиентом. Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *field*  
 Указывает возвращаемое поле *srvproc*.  
  
|Поле|Описание|Тип возвращаемых данных|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|Код языка сообщения текущего сеанса.|ULONG*|  
|SRV_INSTANCENAME|Имя экземпляра (для именованного экземпляра), иначе возвращает значение NULL.|WCHAR*|  
  
 *len*  
 Указатель на переменную типа **int**, которая содержит длину возвращенного значения *field* в байтах. Если значение *len* равно NULL, длина не возвращается. Если возвращается значение NULL, то параметру **len* задается значение 0.  
  
## <a name="returns"></a>Возвращает  
 Указатель на данные, тип которых зависит от *field*. Если *len* имеет значение NULL или *srvproc* имеет значение NULL, возвращается значение NULL. Если *field* неизвестно, то возвращается значение NULL. Если возвращается значение NULL, то параметру **len* задается значение 0.  
  
> [!IMPORTANT]  
>  Буфер, возвращенный из сервера, должен быть доступен только для чтения. В противном случае состояние сервера может быть повреждено.  
  
## <a name="remarks"></a>Remarks  
 **Примечание по безопасности.** Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные DLL-библиотеки перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  
