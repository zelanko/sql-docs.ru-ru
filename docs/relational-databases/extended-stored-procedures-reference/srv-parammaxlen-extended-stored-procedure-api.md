---
title: srv_parammaxlen (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_parammaxlen
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_parammaxlen
ms.assetid: 49bfc29d-f76a-4963-b0e6-b8532dfda850
author: rothja
ms.author: jroth
ms.openlocfilehash: 8dfa779a664d398a6fb619bf17bf67bb52ab1bb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005710"
---
# <a name="srv_parammaxlen-extended-stored-procedure-api"></a>srv_parammaxlen (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Возвращает наибольший размер данных параметра вызова удаленной хранимой процедуры. Эта функция заменена функцией **srv_paraminfo**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_parammaxlen (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил вызов удаленной хранимой процедуры). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *\n*  
 Указывает номер параметра. Первый параметр имеет значение 1.  
  
## <a name="returns"></a>Возвращает  
 Наибольшая длина данных параметра в байтах. Если отсутствует *n*-й параметр или удаленная хранимая процедура, то возвращается значение -1.  
  
 Эта функция возвращает следующие значения, если параметр имеет один из следующих [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
|Новые типы данных|Длина входных данных|  
|--------------------|-----------------------|  
|**BITN**|**Null:** 1<br /><br /> **Ноль:** 1<br /><br /> **>= 255:** Н/Д<br /><br /> **<255:** Н/Д|  
|**BIGVARCHAR**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGCHAR**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGBINARY**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**BIGVARBINARY**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NCHAR**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**NVARCHAR**|**Null:** 255<br /><br /> **Нуль:** 255<br /><br /> **>= 255:** 255<br /><br /> **<255:** 255|  
|**ТИПЫ**|**Null:** -1<br /><br /> **Ноль:** -1<br /><br /> **>= 255:** -1<br /><br /> 255:-1 ** \<**|  
  
## <a name="remarks"></a>Remarks  
 У каждого параметра удаленной хранимой процедуры есть максимальная и реальная длина данных. Для стандартных типов данных с фиксированной длиной, которые не поддерживают значений NULL, реальная и максимальная длина одинаковы. У типов данных переменной длины эти длины могут быть разными. Например, параметр, объявленный как **varchar(30)**, может иметь данные длиной всего 10 байт. Фактическая длина параметра — 10, а максимальная — 30. Функция **srv_parammaxlen** возвращает максимальную длину данных удаленной хранимой процедуры. Чтобы получить фактическую длину параметра, используйте функцию **srv_paramlen**.  
  
 Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров передается по имени, а часть — по позиции, возникает ошибка. Обработчик SRV_RPC по-прежнему вызывается, однако он отображается так, как если бы не имел параметров, а функция **srv_rpcparams** возвращает 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [API srv_paraminfo &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [API srv_rpcparams &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
