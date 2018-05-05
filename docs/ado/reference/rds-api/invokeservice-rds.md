---
title: InvokeService (RDS) | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InvokeService [RDS]
ms.assetid: ad45c676-ec7e-4a3a-9a6b-a54f75eb3012
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a78c815f75b5e30713e0b7f9e5b7ec83c4c3eb6d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Методы службы удаленных рабочих столов](../../../ado/reference/rds-api/rds-methods.md)


