# aicore-pipelines
Prerequisites:
  1. AI Core inštancia na BTP
  2. Vytvorený Service key
  3. Rozbehnutý Docker lokálne

Pre pripojenie na AI Core pomocou SDK: 
  1. pip install ai-core-sdk
  2. pip install notebook
  Pokial bude problem s notebook => Registry Editor->HKEY_LOCAL_MACHINE->SYSTEM->CurrentControlSet->Control->FileSystem->LongPathsEnabled->Nastavit na 1 a opakovat instalaciu
  3. jupyter notebook / python -m notebook

Vytvorenie klienta v Pythone
  #nacitaj kniznicu 
  from ai_core_sdk.ai_core_v2_client import AICoreV2Client
  
  #vytvor spojenie na AI Core
  ai_core_client = AICoreV2Client(
      base_url = "<AI_API_URL>" + "/v2", # Momentalna verzia AI Core
      auth_url=  "<URL>" + "/oauth/token", # Suffix to add
      client_id = "<client_id>",
      client_secret = "<clientsecret>"
  )
  
  response = ai_core_client.repositories.query()
  print(response.count) # pokial vypise error, je potrebne skontrolovat predosle kroky
