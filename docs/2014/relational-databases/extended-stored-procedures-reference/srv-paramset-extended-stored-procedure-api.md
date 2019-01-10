---
title: srv_paramset (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_paramset
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 00645f619a89010bb4e2b112d50e00cbc6f40dce
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360876"
---
# <a name="srvparamset-extended-stored-procedure-api"></a>srv_paramset (API-интерфейс расширенных хранимых процедур)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Устанавливает значение возвратного параметра вызова удаленной хранимой процедуры. Эта функция заменена функцией **srv_paramsetoutput**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил вызов удаленной хранимой процедуры). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *n*  
 Указывает номер параметра, который должен быть задан. Первый параметр имеет значение 1.  
  
 *data*  
 Указатель на значение данных, которое должно быть отправлено назад клиенту, как возвратный параметр удаленной хранимой процедуры.  
  
 *len*  
 Указывает фактическую длину данных, которые должны быть возвращены. Если тип данных параметра имеет постоянную длину и не допускает значений NULL (например, *srvbit* или *srvint1*), параметр *len* не учитывается.  
  
## <a name="returns"></a>Возвращает  
 SUCCEED, если значение параметра было успешно установлено; в противном случае — FAIL. Значение FAIL возвращается, если удаленной хранимой процедуры сейчас не существует, если у нее нет параметра с номером *n*, если параметр не является возвращаемым или если аргумент *len* недопустимый.  
  
 Если *len* имеет значение 0, то возвращается NULL. Единственным способом возвратить значение NULL клиенту является задание параметру *len* значения 0.  
  
 Если параметр принадлежит к одному из типов данных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], то эта функция возвращает следующие значения.  
  
|Новые типы данных|Длина возвращаемых данных|  
|--------------------|------------------------|  
|`BITN`|**NULL:** *len* = 0, data = IG, RET = 0<br /><br /> **НУЛЬ:** Н/Д<br /><br /> **> = 255:** Н/Д<br /><br /> **< 255:** Н/Д|  
|`BIGVARCHAR`|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|`BIGCHAR`|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|`BIGBINARY`|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|`BIGVARBINARY`|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|NCHAR|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|NVARCHAR|**NULL:** *len* = 0, data = IG, RET = 1<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = max8k, data = valid, RET = 0<br /><br /> **<255:** *len* = <8k, data = valid, RET = 1|  
|`NTEXT`|**NULL:** *len* = IG, data = IG, RET = 0<br /><br /> **ZERO:** *len* = IG, data = IG, RET = 0<br /><br /> **>=255:** *len* = IG, data = IG, RET = 0<br /><br /> **\<255:** *len* = IG, data = IG, RET = 0|  
|RET = значение, возвращаемое srv_paramset||  
|IG = значение будет пропущено||  
|valid = любой допустимый указатель на данные||  
  
## <a name="remarks"></a>Примечания  
 Параметры содержат данные, передаваемые между клиентами и приложением с удаленной хранимой процедурой. Клиент может указать некоторые параметры в качестве возвращаемых. Эти возвращаемые параметры могут содержать значения, которые серверное приложение служб Open Data Services данных передает клиенту. Использование возвращаемых параметров аналогично передаче параметров по ссылке.  
  
 Возвращаемое значение невозможно задать параметру, который не был запущен как возвращаемый параметр. Определить, как был вызван параметр, можно с помощью функции **srv_paramstatus**.  
  
 Эта функция задает параметру возвращаемое значение, но она не отправляет это значение клиенту. Все возвращаемые параметры, независимо от того, были ли их возвращаемые значения заданы с помощью функции **srv_paramset** или нет, автоматически отправляются клиенту при вызове функции **srv_senddone** с установленным флагом состояния SRV_DONE_FINAL.  
  
 Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров передается по имени, а часть — по позиции, возникает ошибка. Обработчик SRV_RPC по-прежнему вызывается, однако он отображается так, как если бы не имел параметров, а функция **srv_rpcparams** возвращает 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также  
 [srv_paramsetoutput (интерфейс API расширенных хранимых процедур)](srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
