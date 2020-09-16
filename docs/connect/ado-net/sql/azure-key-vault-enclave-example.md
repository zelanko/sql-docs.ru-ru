---
description: Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами
title: Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 07/09/2020
ms.reviewer: v-kaywon
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: karinazhou
ms.author: v-jizho2
ms.openlocfilehash: 1cb8669a14039f7155e6c31fce62de44c1fac03a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438646"
---
# <a name="example-demonstrating-use-of-azure-key-vault-provider-with-always-encrypted-enabled-with-secure-enclaves"></a>Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted с безопасными анклавами

[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[!INCLUDE [appliesto-netfx-netcore-xxxx-md](../../../includes/appliesto-netfx-netcore-xxxx-md.md)]

В этом примере демонстрируется использование поставщика Azure Key Vault при доступе к зашифрованным столбцам.

[!code-csharp [Azure Key Vault Provider with Enclave Example#1](~/../sqlclient/doc/samples/AzureKeyVaultProviderWithEnclaveProviderExample.cs#1)]

> [!NOTE]
> Always Encrypted с безопасными анклавами поддерживается только в Windows.

## <a name="see-also"></a>См. также:

- [Пример использования поставщика Azure Key Vault с поддержкой Always Encrypted](azure-key-vault-example.md)
- [Руководство. Разработка приложения .NET с помощью Always Encrypted с безопасными анклавами](tutorial-always-encrypted-enclaves-develop-net-apps.md)
- [Использование Always Encrypted с поставщиком данных Microsoft .NET для SQL Server](sqlclient-support-always-encrypted.md)
