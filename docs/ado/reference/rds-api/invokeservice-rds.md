---
title: Инвокесервице (RDS) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1ead0a42c0c5239a0f3bb4cafecb584788e06832
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82751910"
---
# <a name="invokeservice-rds"></a>InvokeService (служба удаленных рабочих столов)
Возвращает указатель на запрошенный интерфейс в более совместимой версии объекта.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.InvokeService(REFID riid, IUknown* punkNotSoFunctionalInterface, IUknown** ppunkMoreFunctionalInterface) As HRESULT  
```  
  
#### <a name="parameters"></a>Параметры  
 *riid*  
  
 окне Идентификатор запрашиваемого интерфейса.  
  
 *пункнотсофунктионалинтерфаце*  
  
 окне Менее совместимый исходный объект.  
  
 *ппункморефунктионалинтерфаце*  
  
 заполняет Адрес переменной указателя, получающей указатель интерфейса, запрошенный в *riid*. После успешного возврата параметр *ппункморефунктионалинтерфаце* содержит указатель на объект в виде запрошенного интерфейса. Если объект не поддерживает интерфейс, указанный в *riid*, *ППУНКМОРЕФУНКТИОНАЛИНТЕРФАЦЕ* имеет значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, был ли успешно вызван метод **инвокесервице** .  
  
## <a name="remarks"></a>Примечания  
 Реализация обработчика курсора RDS **инвокесервице** принимает входной набор строк (или несколько результатов), заполняет обработчик курсора из входного набора строк, а затем возвращает указатель на себя.  
  
## <a name="applies-to"></a>Применяется к  
 [Интерфейс IRDSService (служба удаленных рабочих столов)](../../../ado/reference/rds-api/irdsservice-interface-rds.md)  
  
## <a name="see-also"></a>См. также  
 [Методы службы удаленных рабочих столов](../../../ado/reference/rds-api/rds-methods.md)


