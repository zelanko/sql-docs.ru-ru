---
title: "Определяемые пользователем типы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ed2b0bb8227a1b430bcd30b1d41460862c8db325
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="user-defined-types"></a>Определяемые пользователем типы
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Определяемые пользователем типы (UDT) впервые появились в [!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)] позволяет разработчику возможность расширить серверную систему скалярных типов путем хранения объектов среды CLR в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Определяемые пользователем типы могут содержать несколько элементов и поведение может, в отличие от традиционных псевдонимов типов данных, которые состоят из одного [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] системный тип данных. Ранее размер определяемых пользователем типов был ограничен 8 килобайтами. В [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)], была добавлена поддержка определяемых пользователем типов данных, размер которых превышает 64 килобайта. Начиная с версии 3.0 драйвер JDBC также поддерживает определяемые пользователем типы с размером более 64 килобайт при указании формата UserDefined.  
  
 Поведение определяемых пользователем типов с размером, не превышающим 8000 байт, не изменилось, но теперь поддерживаются более крупные, определяемые пользователем типы, для которых сообщается размер unlimited.  
  
## <a name="see-also"></a>См. также:  
 [Основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
