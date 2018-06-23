---
title: srv_pfieldex (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
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
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 77ce8845cce63eb942c57c45d60dc56ce500f73b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101066"
---
# <a name="srvpfieldex-extended-stored-procedure-api"></a>srv_pfieldex (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
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
  
## <a name="remarks"></a>Примечания  
 **Примечание по безопасности.** Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные DLL-библиотеки перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
  