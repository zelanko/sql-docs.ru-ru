---
title: srv_paraminfo (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paraminfo
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paraminfo
ms.assetid: ee2afd4e-0d91-462b-9403-98d481546330
author: rothja
ms.author: jroth
ms.openlocfilehash: 85efd235861522754cbcdc209d6cf28558907d76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68058776"
---
# <a name="srv_paraminfo-extended-stored-procedure-api"></a>srv_paraminfo (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Возвращает сведения о параметре. Эта функция заменяет следующие: [srv_paramtype](../../relational-databases/extended-stored-procedures-reference/srv-paramtype-extended-stored-procedure-api.md), [srv_paramlen](../../relational-databases/extended-stored-procedures-reference/srv-paramlen-extended-stored-procedure-api.md), [srv_parammaxlen](../../relational-databases/extended-stored-procedures-reference/srv-parammaxlen-extended-stored-procedure-api.md) и [srv_paramdata](../../relational-databases/extended-stored-procedures-reference/srv-paramdata-extended-stored-procedure-api.md). **srv_paraminfo** поддерживает типы данных в [типах данных](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md) и данные нулевой длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_paraminfo (  
SRV_PROC *  
srvproc  
,  
int  
n  
,  
BYTE *  
pbType  
,  
ULONG *  
pcbMaxLen  
,  
ULONG *  
pcbActualLen  
,  
BYTE *  
pbData  
,  
BOOL *  
pfNull  
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Дескриптор для клиентского соединения.  
  
 *\n*  
 Порядковый номер устанавливаемого столбца. Первый параметр имеет значение 1.  
  
 *пбтипе*  
 Тип данных параметра.  
  
 *пкбмакслен*  
 Указатель на максимальную длину параметра.  
  
 *pcbActualLen*  
 Указатель на фактическую длину параметра. Значение 0 (\**pcbActualLen* == 0) указывает на данные нулевой длины, если значение **pfNull* равно FALSE.  
  
 *pbData*  
 Указатель на буфер данных параметра. Если значение *pbData* не равно NULL, интерфейс API расширенных хранимых процедур записывает \**pcbActualLen* байт данных в \**pbData*. Если *pbData* имеет значение NULL, данные в \**pbData* не записываются, но функция возвращает \**pbType*, \**pcbMaxLen*, \**pcbActualLen* и **pfNull*. Управление памятью для этого буфера должно осуществляться приложением.  
  
 *pfNull*  
 Указатель на флаг null **pfNull* имеет значение true, если параметр равен null.  
  
## <a name="returns"></a>Возвращает  
 При успешном получении сведений о параметре возвращается значение SUCCEED; в иных случаях – значение FAIL. Значение FAIL возвращается, если удаленной хранимой процедуры сейчас не существует или у нее нет параметра с номером *n*.  
  
## <a name="remarks"></a>Remarks  
 **Примечание по безопасности** Следует тщательно проанализировать исходный код расширенных хранимых процедур, а также протестировать скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по программированию расширенных хранимых процедур](../../relational-databases/extended-stored-procedures-reference/database-engine-extended-stored-procedures-reference.md)  
  
  
