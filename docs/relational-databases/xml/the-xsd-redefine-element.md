---
title: 'Элемент &lt;xsd: redefine&gt; | Документация Майкрософт'
description: Сведения о поддержке элемента W3C XSD redefine и обновлении схемы XML или ее компонентов.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4f2791ea8a8cae425ae7839a7af2d722e8cfe8a6
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85729863"
---
# <a name="the-ltxsdredefinegt-element"></a>Элемент &lt;xsd:redefine&gt;
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Элемент W3C XSD **redefine** обеспечивает поддержку переопределения компонентов схемы. Однако поддержка этой директивы является потенциально затратной в смысле производительности, а также требует, чтобы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно проверялись все экземпляры типа данных **xml** , связанные с переопределенной схемой. Поэтому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает этот элемент. XML-схемы, которые включают элемент **\<xsd:redefine>** , будут отклонены сервером.  
  
 Чтобы обновить схему или ее компоненты, вместо этого можно сделать следующее.  
  
1.  Создайте новую коллекцию XML-схем с измененными компонентами схемы.  
  
2.  Повторно введите все типы данных **xml** (XML DT), в которых применяется переопределяемая коллекция схем XML, таким образом, чтобы в них использовалась новая коллекция. Для повторного ввода столбцов воспользуйтесь параметром ALTER COLUMN команды ALTER TABLE или измените ограничения коллекции XML-схемы по переменным или параметрам.  
  
3.  Удалите старую версию коллекции XML-схем.  

## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций схем XML на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
