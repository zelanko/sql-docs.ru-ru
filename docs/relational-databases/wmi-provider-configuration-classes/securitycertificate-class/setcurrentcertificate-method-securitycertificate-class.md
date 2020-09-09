---
description: Метод SetCurrentCertificate (класс SecurityCertificate)
title: Метод SetCurrentCertificate (класс securitycertificate)
ms.custom: seo-lt-2019
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetCurrentCertificate Method (SecurityCertificate Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetCurrentCertificate method
ms.assetid: 04b1a76a-932d-4824-8506-e346afe7554e
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 504ee5369f193360a4e0705f9c9a1e352dbb23ff
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545280"
---
# <a name="setcurrentcertificate-method-securitycertificate-class"></a>Метод SetCurrentCertificate (класс SecurityCertificate)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Задает текущий сертификат безопасности.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.SetCurrentCertificate(SHA , SQLInstance)  
```  
  
## <a name="parts"></a>Компоненты  
 *object*  
 Объект [класса SecurityCertificate](../../../relational-databases/wmi-provider-configuration-classes/securitycertificate-class/securitycertificate-class.md) , представляющий сертификат безопасности.  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание|  
|---------------|-----------------|  
|*SHA*|Строковое значение, определяющее отпечаток безопасного хэш-алгоритма (SHA) для нужного сертификата безопасности.|  
|*SQLInstance*|Строковое значение, указывающее экземпляр, для которого необходим сертификат.|  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, равное 0, если служба изменена успешно, и 1, если запрос не поддерживается. Любое другое значение указывает на ошибку.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Конфигурирование сетевых протоколов сервера и сетевых библиотек](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
