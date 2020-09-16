---
description: Метод setApplicationName (SQLServerDataSource)
title: Метод setApplicationName (SQLServerDataSource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setApplicationName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 24d6e48d-53c4-4da2-a6de-1cdff463c9cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e237100c0c1da4ad9188da943412891d808a735c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432666"
---
# <a name="setapplicationname-method-sqlserverdatasource"></a>Метод setApplicationName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает имя приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setApplicationName(java.lang.String applicationName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *applicationName*  
  
 Значение типа **String**, содержащее имя приложения.  
  
## <a name="remarks"></a>Remarks  
 Имя приложения используется для идентификации определенных приложений в различных средствах профилирования и ведения журналов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если имя приложения не задано, метод getApplicationName возвращает нелокализованную строку "[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]".  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
