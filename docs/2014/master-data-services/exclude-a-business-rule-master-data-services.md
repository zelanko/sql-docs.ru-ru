---
title: Исключение бизнес-правила (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- master-data-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- business rules [Master Data Services], excluding
ms.assetid: bdbc9df0-23f7-40b9-8aba-4445c1482580
caps.latest.revision: 4
author: leolimsft
ms.author: lle
manager: craigg
ms.openlocfilehash: a51bf291ebdf7904fbce836cfaddb3cceb5e17cc
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37172951"
---
# <a name="exclude-a-business-rule-master-data-services"></a>Исключение бизнес-правила (службы Master Data Services)
  В [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]исключите бизнес-правило, если его не следует удалять без возможности восстановления и отсутствует необходимость проверки данных на соответствие этому бизнес-правилу.  
  
## <a name="prerequisites"></a>предварительные требования  
 Для выполнения этой процедуры:  
  
-   необходимо иметь разрешение на доступ к функциональной области **Администрирование системы** ;  
  
-   необходимо быть администратором модели. Дополнительные сведения см. в статье [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).  
  
### <a name="to-exclude-a-business-rule"></a>Исключение бизнес-правила  
  
1.  В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]щелкните область **Администрирование системы**.  
  
2.  В строке меню выберите **Управление** и щелкните **Бизнес-правила**.  
  
3.  На странице **Обслуживание бизнес-правил** выберите модель из списка **Модель** .  
  
4.  Выберите сущность из списка **Сущность** .  
  
5.  Из **тип члена** выберите тип элемента.  
  
6.  Выберите из списка **Атрибут** атрибут или оставьте **Все**по умолчанию.  
  
7.  В сетке, в строке бизнес-правила, установите флажок в **исключить** столбца. Значение в **состояние** столбец **ожидается исключение**.  
  
8.  Нажмите кнопку **Опубликовать бизнес-правила**.  
  
9. В диалоговом окне подтверждения нажмите кнопку **ОК**. Значение в **состояние** столбец **исключенные**.  
  
## <a name="see-also"></a>См. также  
 [Удалить бизнес-правило &#40;службы Master Data Services&#41;](../../2014/master-data-services/delete-a-business-rule-master-data-services.md)   
 [Создание и публикация бизнес-правила (службы Master Data Services)](../../2014/master-data-services/create-and-publish-a-business-rule-master-data-services.md)   
 [Бизнес-правила &#40;службы Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
