---
title: Свойства псевдонима (вкладка "Псевдоним")
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 2d1498e2-129c-4ce7-88e5-408e4037243c
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 53bb19934209ee501c76317e102e5b1fcae28c4d
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75306600"
---
# <a name="ltaliasgt-properties-alias-tab"></a>Свойства &lt;псевдонима&gt; (вкладка "Псевдоним")

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Псевдоним является альтернативным именем, которое можно использовать для создания соединения. Псевдоним инкапсулирует необходимые элементы строки соединения и представляет их с помощью имени, выбранного пользователем. Используйте страницу **Псевдоним** в диалоговом окне **\<** Свойства <**Псевдоним>** , чтобы просматривать или указывать элементы строки подключения псевдонима.

## <a name="options"></a>Параметры

**Имя псевдонима**

Имя (псевдоним), которое будет использоваться для ссылки на это соединение.  

**Имя канала** / **Номер порта**  

Дополнительные элементы строки подключения. Имя этого поля зависит от выбранного протокола. Примеры см. в перечисленных ниже разделах.  

**протокол**;

Протокол, используемый для соединения.

**Server**

Имя экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], к которому выполняется подключение.  

## <a name="see-also"></a>См. также:

- [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
- [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)
- [Создание допустимой строки подключения, использующей протокол именованных каналов](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)