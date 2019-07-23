---
title: Метод setApplicationName (SQLServerDataSource) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f0f91762dd168f4136a4a476b47dfe36b749e16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975563"
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
  
  
