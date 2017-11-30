---
title: "srv_paramlen (интерфейс API расширенных хранимых процедур) | Документы Майкрософт"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: extended-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: reference
apiname: srv_paramlen
apilocation: opends60.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords: srv_paramlen
ms.assetid: d1fe92ff-cad6-4396-8216-125e5642e81e
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9f3f7a3a3b8f0cae6813cbc571ad038f1e673a41
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="srvparamlen-extended-stored-procedure-api"></a>srv_paramlen (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает длину данных параметра вызова удаленной хранимой процедуры. Эта функция заменена функцией **srv_paraminfo**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_paramlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил вызов удаленной хранимой процедуры). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *n*  
 Указывает номер параметра. Первый параметр имеет значение 1.  
  
## <a name="returns"></a>Возвращает  
 Фактическая длина данных параметра в байтах. Если *n*-й параметр или удаленная хранимая процедура отсутствует, то возвращается значение –1. Если *n*-й параметр равен NULL, то возвращается значение 0.  
  
 Эта функция возвращает указанные ниже значения, если параметр принадлежит к одному из перечисленных ниже системных типов данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].  
  
|Новые типы данных|Длина входных данных|  
|--------------------|-----------------------|  
|**BITN**|**NULL:** 1<br /><br /> **ZERO:** 1<br /><br /> **>=255:** недоступно<br /><br /> **<255:** недоступно|  
|**BIGVARCHAR**|**NULL:** 0<br /><br /> **ZERO:** 1<br /><br /> **>=255:** 255<br /><br /> **<255:** фактическое значение *len*|  
|**BIGCHAR**|**NULL:** 0<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**BIGBINARY**|**NULL:** 0<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**BIGVARBINARY**|**NULL:** 0<br /><br /> **ZERO:** 1<br /><br /> **>=255:** 255<br /><br /> **<255:** фактическое значение *len*|  
|**NCHAR**|**NULL:** 0<br /><br /> **ZERO:** 255<br /><br /> **>=255:** 255<br /><br /> **<255:** 255|  
|**NVARCHAR**|**NULL:** 0<br /><br /> **ZERO:** 1<br /><br /> **>=255:** 255<br /><br /> **<255:** фактическое значение *len*|  
|**NTEXT**|**NULL:** –1<br /><br /> **ZERO:** –1<br /><br /> **>=255:** –1<br /><br /> **\<255:** –1|  
  
 \* фактическое значение *len* = длина многобайтовой символьной строки (cch)  
  
## <a name="remarks"></a>Замечания  
 У каждого параметра удаленной хранимой процедуры есть максимальная и реальная длина данных. Для стандартных типов данных с фиксированной длиной, которые не поддерживают значений NULL, реальная и максимальная длина одинаковы. У типов данных переменной длины эти длины могут быть разными. Например, параметр, объявленный как **varchar(30)**, может иметь данные длиной всего 10 байт. Фактическая длина параметра — 10, а максимальная — 30. Функция **srv_paramlen** возвращает фактическую длину данных в байтах удаленной хранимой процедуры. Для получения максимальной длины данных параметра используется функция **srv_parammaxlen**.  
  
 Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров передается по имени, а часть — по позиции, возникает ошибка. Обработчик SRV_RPC по-прежнему вызывается, однако он отображается так, как если бы не имел параметров, а **srv_rpcparams** возвращает 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [srv_paraminfo (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [srv_rpcparams (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
