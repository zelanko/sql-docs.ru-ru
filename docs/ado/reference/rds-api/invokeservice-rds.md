---
title: InvokeService (служба удаленных рабочих СТОЛОВ) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 86ebb27ebdc5de5a045304afe45cd8653e491827
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963862"
---
# <a name="invokeservice-rds"></a>InvokeService (служба удаленных рабочих столов)
Возвращает указатель на запрошенный интерфейс на более мощным версии объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ, больше не включаются в операционной системе Windows (см. в разделе Windows 8 и [настольная книга по совместимости Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будет поддерживаться в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ, следует перевести [WCF-сервиса данных](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Параметры  
 *riid*  
  
 [in] Идентификатор запрашиваемого интерфейса.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] Меньшими возможностями исходный объект.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] Адрес переменной указателя, получающей указатель интерфейса, запрашиваемый в *riid*. При успешном возвращении *ppunkMoreFunctionalInterface* параметр содержит запрошенный указатель интерфейса на объект. Если объект не поддерживает интерфейс, указанный в *riid*, *ppunkMoreFunctionalInterface* имеет значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, если вызов **InvokeService** метод был выполнен успешно.  
  
## <a name="remarks"></a>Примечания  
 Реализация ядра курсора RDS **InvokeService** принимает входной набор строк (или несколько объектов результатов), заполняет в ядре курсора из входного набора строк и затем возвращает указатель на себя.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс IRDSService (служба удаленных рабочих столов)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Методы службы удаленных рабочих столов](../../../ado/reference/rds-api/rds-methods.md)


