-- Lista de palavras possíveis
local palavras = {"banana", "lua", "computador", "teclado", "chocolate"}

-- Escolhe uma palavra aleatória
math.randomseed(os.time())
local palavra = palavras[math.random(#palavras)]

local letras_descobertas = {}
local letras_tentadas = {}
local tentativas_max = 6
local tentativas_erradas = 0

-- Inicializa letras descobertas com "_"
for i = 1, #palavra do
  letras_descobertas[i] = "_"
end

-- Função para mostrar estado atual
local function mostrar_progresso()
  print("\nPalavra: " .. table.concat(letras_descobertas, " "))
  print("Tentativas erradas: " .. tentativas_erradas .. "/" .. tentativas_max)
  print("Letras já tentadas: " .. table.concat(letras_tentadas, ", "))
end

-- Função para verificar se venceu
local function venceu()
  return table.concat(letras_descobertas, "") == palavra
end

-- Loop principal
while tentativas_erradas < tentativas_max do
  mostrar_progresso()
  io.write("Digite uma letra: ")
  local letra = io.read():lower()

  if #letra ~= 1 then
    print("Digite apenas UMA letra!")
  elseif table.concat(letras_tentadas):find(letra) then
    print("Você já tentou essa letra!")
  else
    table.insert(letras_tentadas, letra)
    local acertou = false

    for i = 1, #palavra do
      if palavra:sub(i, i) == letra then
        letras_descobertas[i] = letra
        acertou = true
      end
    end

    if not acertou then
      tentativas_erradas = tentativas_erradas + 1
      print("Letra errada! 😬")
    else
      print("Boa! Letra correta! 🎉")
    end

    if venceu() then
      print("\n🎉 Você venceu! A palavra era: " .. palavra)
      break
    end
  end
end

if not venceu() then
  print("\n💀 Você perdeu! A palavra era: " .. palavra)
end
