---
title: 'Элемент &lt;xsd: redefine&gt; | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- xsd:redefine element
ms.assetid: 5f3e9b65-f10e-4db2-a62c-b270ac11d04e
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 4ca94410d7011c30de0a5481451337d11fa57120
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195746"
---
# <a name="the-ltxsdredefinegt-element"></a>Элемент &lt;xsd:redefine&gt;
  Элемент W3C XSD **redefine** обеспечивает поддержку переопределения компонентов схемы. Однако поддержка этой директивы является потенциально затратной в смысле производительности, а также требует, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] повторно проверялись все экземпляры `xml` тип данных, связанные с переопределенной схемой. Поэтому [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает этот элемент. XML-схемы, которые включают элемент **\<xsd:redefine>**, будут отклонены сервером.  
  
 Чтобы обновить схему или ее компоненты, вместо этого можно сделать следующее.  
  
1.  Создайте новую коллекцию XML-схем с измененными компонентами схемы.  
  
2.  Повторно введите все типы данных `xml` (XML DT), в которых используется переопределяемая коллекция XML-схем, таким образом, чтобы в них использовалась новая коллекция XML-схем. Для повторного ввода столбцов воспользуйтесь параметром ALTER COLUMN команды ALTER TABLE или измените ограничения коллекции XML-схемы по переменным или параметрам.  
  
3.  Удалите старую версию коллекции XML-схем.  
  
## <a name="see-also"></a>См. также  
 [Требования и ограничения для коллекций схем XML на сервере](requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  