---
title: "InvokeService (RDS) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
helpviewer_keywords: InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: be188df1a61cfd398644ba42af5d32605d501919
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="invokeservice-rds"></a>InvokeService (RDS)
Возвращает указатель на запрошенный интерфейс на более производительные версию объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, серверные компоненты служб удаленных рабочих СТОЛОВ больше не включаются в операционной системе Windows (в разделе Windows 8 и [руководство по Windows Server 2012 совместимости](https://www.microsoft.com/en-us/download/details.aspx?id=27416) для получения дополнительных сведений). Клиентские компоненты служб удаленных рабочих СТОЛОВ будут удалены в будущих версиях Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие служб удаленных рабочих СТОЛОВ необходимо перенести в [службы данных WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Параметры  
 *riid*  
  
 [in] Идентификатор запрашиваемого интерфейса.  
  
 *punkNotSoFunctionalInterface*  
  
 [in] Исходный объект меньшими возможностями.  
  
 *ppunkMoreFunctionalInterface*  
  
 [out] Адрес переменной указателя, получающей указатель интерфейса, запрашиваемый в *riid*. После успешного возврата *ppunkMoreFunctionalInterface* параметр содержит указатель на объект запрошенный интерфейс. Если объект не поддерживает интерфейс, заданный в *riid*, *ppunkMoreFunctionalInterface* имеет значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, если вызов **InvokeService** метод выполнен успешно.  
  
## <a name="remarks"></a>Замечания  
 Реализация ядра курсора служб удаленных рабочих СТОЛОВ **InvokeService** принимает входной набор строк (или несколько объектов результатов), заполняет ядро курсора из входного набора строк и затем возвращает указатель на себя.  
  
## <a name="applies-to"></a>Объект применения  
 [Интерфейс IRDSService (служба удаленных рабочих столов)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>См. также:  
 [Методы службы удаленных рабочих столов](../../../ado/reference/rds-api/rds-methods.md)


