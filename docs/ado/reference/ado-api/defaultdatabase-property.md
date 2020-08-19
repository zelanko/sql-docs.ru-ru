---
description: Свойство DefaultDatabase
title: DefaultDatabase, свойство | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::DefaultDatabase
helpviewer_keywords:
- DefaultDatabase property
ms.assetid: 41e8a8dd-e69c-4a09-8736-93502e01961c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7e16a5a5bc3a711477cca1507c889bd15e0f37a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444196"
---
# <a name="defaultdatabase-property"></a>Свойство DefaultDatabase
Указывает базу данных по умолчанию для объекта [соединения](../../../ado/reference/ado-api/connection-object-ado.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает **строковое** значение, результатом которого является имя базы данных, доступной из поставщика.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **DefaultDatabase** , чтобы задать или вернуть имя базы данных по умолчанию для конкретного объекта **соединения** .  
  
 При наличии базы данных по умолчанию строки SQL могут использовать неполный синтаксис для доступа к объектам в этой базе данных. Для доступа к объектам в базе данных, отличной от указанной в свойстве **DefaultDatabase** , необходимо указать имена объектов с нужным именем базы данных. При подключении поставщик будет записывать сведения о базе данных по умолчанию в свойство **DefaultDatabase** . Некоторые поставщики разрешают только одну базу данных на одно соединение. в этом случае изменить свойство **DefaultDatabase** нельзя.  
  
 Некоторые источники данных и поставщики могут не поддерживать эту функцию и могут возвращать ошибку или пустую строку.  
  
> [!NOTE]
>  **Использование удаленной службы данных** Это свойство недоступно для объекта **подключения** на стороне клиента.  
  
## <a name="applies-to"></a>Применение  
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример свойств provider и DefaultDatabase (Visual Basic)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vb.md)   
 [Примеры свойств Provider и DefaultDatabase (Visual C++)](../../../ado/reference/ado-api/provider-and-defaultdatabase-properties-example-vc.md)   
