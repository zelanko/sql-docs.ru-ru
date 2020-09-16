---
description: Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted
title: Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted | Документация Майкрософт
ms.custom: ''
ms.date: 10/18/2019
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: b0f389a822b3fcc37572b34a17cd5780f1091bd4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438666"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted"></a>Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted

[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-xxxx-md.md)]

В этом примере демонстрируется использование поставщика Azure Key Vault при доступе к зашифрованным столбцам.

[!code-csharp [AKVProvider Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderExample.cs#1)]

## <a name="see-also"></a>См. также:

- [Example demonstrating use of Azure Key Vault provider with Always Encrypted enabled with Secure Enclaves](azure-key-vault-enclave-example.md) (Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами)
- [Руководство. Разработка приложения .NET с помощью Always Encrypted с безопасными анклавами](tutorial-always-encrypted-enclaves-develop-net-apps.md)
- [Использование Always Encrypted с поставщиком данных Microsoft .NET для SQL Server](sqlclient-support-always-encrypted.md)
