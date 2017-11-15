---
title: "Элемент &lt;xsd: redefine&gt; | Документация Майкрософт"
ms.custom: SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
caps.latest.revision: "14"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80d00134f8ebfa1360551b8d10b28650c217388f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="the-ltxsdredefinegt-element"></a>Элемент &lt;xsd:redefine&gt;
  Элемент W3C XSD **redefine** обеспечивает поддержку переопределения компонентов схемы. Однако поддержка этой директивы является потенциально затратной в смысле производительности, а также требует, чтобы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно проверялись все экземпляры типа данных **xml** , связанные с переопределенной схемой. Поэтому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает этот элемент. XML-схемы, которые включают элемент **\<xsd:redefine>**, будут отклонены сервером.  
  
 Чтобы обновить схему или ее компоненты, вместо этого можно сделать следующее.  
  
1.  Создайте новую коллекцию XML-схем с измененными компонентами схемы.  
  
2.  Повторно введите все типы данных **xml** (XML DT), в которых применяется переопределяемая коллекция схем XML, таким образом, чтобы в них использовалась новая коллекция. Для повторного ввода столбцов воспользуйтесь параметром ALTER COLUMN команды ALTER TABLE или измените ограничения коллекции XML-схемы по переменным или параметрам.  
  
3.  Удалите старую версию коллекции XML-схем.  
  
## <a name="see-also"></a>См. также:  
 [Требования и ограничения для коллекций XML-схем на сервере](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
