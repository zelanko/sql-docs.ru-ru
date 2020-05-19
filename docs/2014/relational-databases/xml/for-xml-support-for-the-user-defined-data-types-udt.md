---
title: Поддержка FOR XML для определяемых пользователем типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- UDTs [SQL Server], XML
- user-defined types [SQL Server], XML
ms.assetid: 354e2150-fa2a-4583-b1aa-6b78ae4378b6
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 25156dd240c90b7cc50cc44fba90125f5c6eab85
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2020
ms.locfileid: "82702716"
---
# <a name="for-xml-support-for-the-user-defined-data-types-udt"></a>Поддержка FOR XML для определяемых пользователем типов данных
  FOR XML не поддерживает определяемые пользователем типы данных (UDT) среды CLR.  
  
 Чтобы использовать FOR XML с определяемыми пользователем типами данных среды CRL, убедитесь, что у этих типов данных имеется XML-сериализация, а в предложении SELECT FOR XML используйте явное приведение к типу XML.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка FOR XML для различных типов данных SQL Server](for-xml-support-for-various-sql-server-data-types.md)  
  
  
