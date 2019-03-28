---
title: Создание, изменение и удаление вторичных селективных XML-индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
ms.assetid: 45128105-833b-40a9-9cc9-1ae03ac0b52b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b96e0bb7f28349e4d0b0ed5225f9b29e58de982f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536626"
---
# <a name="create-alter-and-drop-secondary-selective-xml-indexes"></a>Создание, изменение и удаление вторичных селективных XML-индексов
  Описание создания нового вторичного селективного XML-индекса, а также изменения или удаления существующего вторичного селективного XML-индекса.  
  
##  <a name="create"></a> Создание вторичного селективного XML-индекса  
  
### <a name="how-to-create-a-secondary-selective-xml-index"></a>Практическое руководство. создать вторичный селективный XML-индекс  
 **Создание вторичного селективного XML-индекса с использованием Transact-SQL**  
 Создание вторичного селективного XML-индекса путем вызова инструкции CREATE XML INDEX. Дополнительные сведения см. в разделе [CREATE XML INDEX &#40;Селективные XML-индексы&#41;] (~ / t-sql/statements/create-xml-index-selective-xml-indexes.  
  
 **Пример**  
  
 В следующем примере создается вторичный селективный XML-индекс с путем `'pathabc'`. Путь к индексу определяется по имени, заданному для него при создании с помощью инструкции CREATE SELECTIVE XML INDEX. Дополнительные сведения см. в разделе [CREATE SELECTIVE XML INDEX (Transact-SQL)](/sql/t-sql/statements/create-selective-xml-index-transact-sql).  
  
```sql  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="alter"></a> Изменение вторичного селективного XML-индекса  
 Инструкция ALTER не поддерживается для вторичных селективных XML-индексов. Чтобы изменить вторичный селективный XML-индекс, удалите существующий индекс и создайте его повторно.  
  
### <a name="how-to-alter-a-secondary-selective-xml-index"></a>Практическое руководство. изменить вторичный селективный XML-индекс  
 **Изменение вторичного селективного XML-индекса с использованием Transact-SQL**  
 1.  Удаление существующего вторичного селективного XML-индекса путем вызова инструкции DROP INDEX. Дополнительные сведения см. в разделе [DROP INDEX (селективные XML-индексы)](../indexes/indexes.md).  
  
2.  Повторное создание индекса с требуемыми параметрами путем вызова инструкции CREATE XML INDEX. Дополнительные сведения см. в разделе [CREATE XML INDEX &#40;Селективные XML-индексы&#41;] (~ / t-sql/statements/create-xml-index-selective-xml-indexes.  
  
 **Пример**  
  
 В следующем примере показан способ изменения вторичного селективного XML-индекса путем его удаления и повторного создания.  
  
```sql  
DROP INDEX filt_sxi_index_c  
  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR  
(  
    pathabc  
)  
```  
  
  
##  <a name="drop"></a> Удаление вторичного селективного XML-индекса  
  
### <a name="how-to-drop-a-secondary-selective-xml-index"></a>Практическое руководство. удалить вторичный селективный XML-индекс  
 **Удаление вторичного селективного XML-индекса с использованием Transact-SQL**  
 Удаление вторичного селективного XML-индекса путем вызова инструкции DROP INDEX. Дополнительные сведения см. в разделе [DROP INDEX (селективные XML-индексы)](../indexes/indexes.md).  
  
 **Пример**  
  
 В следующем примере показана инструкция DROP INDEX.  
  
```sql  
DROP INDEX ssxi_index  
ON tbl  
```  
  
  
## <a name="see-also"></a>См. также  
 [Выборочный XML-индекс (SXI)](selective-xml-indexes-sxi.md)  
  
  
