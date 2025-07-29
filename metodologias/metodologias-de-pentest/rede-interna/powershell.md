# Powershell

Port Scanning

```
# Define o endereço IP alvo
$enderecoIP = "192.168.1.158"

# Define o intervalo de portas para o scan (ajuste conforme necessário para um teste mais rápido)
$portas = 1..1024

# Especifica o caminho do arquivo de saída
$arquivoSaida = "portscan.txt"

# Prepara o arquivo de saída
"Portas abertas no ${enderecoIP}:" | Out-File $arquivoSaida

# Inicializa a variável de progresso
$progresso = 0
$totalPortas = $portas.Count

foreach ($porta in $portas) {
    # Atualiza e exibe a barra de progresso
    $percentComplete = [math]::Round(($progresso / $totalPortas) * 100, 2)
    Write-Progress -PercentComplete $percentComplete -Status "Scanning: $enderecoIP" -Activity "Port Scan Progress" -CurrentOperation "Porta ${porta}"

    $connection = $null

    try {
        # Tenta conectar com um timeout de 1000ms (1 segundo)
        $connection = New-Object System.Net.Sockets.TcpClient($enderecoIP, $porta)
        $connection.ReceiveTimeout = 1000
        $connection.SendTimeout = 1000

        if ($connection.Connected) {
            "Porta ${porta}: Aberta" | Out-File -FilePath $arquivoSaida -Append
        }
    } catch {
        # Não faz nada se a porta estiver fechada
    } finally {
        if ($connection -ne $null) {
            $connection.Close()
        }
    }

    $progresso++
}

Write-Progress -PercentComplete 100 -Status "Scan Completo" -Completed
"Scan completo." | Out-File -FilePath $arquivoSaida -Append
```
