# NINJA-BOT
cmd /k
auth = None
vlocal = "1.0.1" #No deberias cambiar esta variable
vlocal = "1.2.0" #No deberias cambiar esta variable
vactual = requests.get("https://raw.githubusercontent.com/Londiuh/MDJ-bot/master/version.txt")  

print(f'  ')
@@ -47,13 +47,16 @@ class color: #Tabla de colores (aunque tambíen uso colorama)
eval(compile(base64.b64decode('Y3JkMT1UcnVlDQpwcmludChjb2xvci5EQVJLQ1lBTitmIiBcdFx0XHRcdCIrYmFzZTY0LmI2NGRlY29kZSgiVlc1aElHTnZjMkVnYUdWamFHRWdjRzl5SUVWc1RHOXVaR2wxYUE9PSIuZW5jb2RlKCdhc2NpaScpKS5kZWNvZGUoJ2FzY2lpJykp'),'','exec'))
print(f'  ') 

def getTiempesito():
    tiempesito = datetime.datetime.now().strftime('%H:%M:%S')
    return tiempesito
print(color.DARKCYAN + f"Versión: {vlocal}")
time.sleep(0.5)
print(Fore.MAGENTA + f"Buscando actualizaciones...")
print(Fore.MAGENTA + f"[{getTiempesito()}] Buscando actualizaciones...")
time.sleep(0.5)
vactualfix = vactual.text[:-1] #Muy cutre, lo se, yo soy cutre
if vactualfix != vlocal:

print(f'  ')
@@ -47,13 +47,16 @@ class color: #Tabla de colores (aunque tambíen uso colorama)
eval(compile(base64.b64decode('Y3JkMT1UcnVlDQpwcmludChjb2xvci5EQVJLQ1lBTitmIiBcdFx0XHRcdCIrYmFzZTY0LmI2NGRlY29kZSgiVlc1aElHTnZjMkVnYUdWamFHRWdjRzl5SUVWc1RHOXVaR2wxYUE9PSIuZW5jb2RlKCdhc2NpaScpKS5kZWNvZGUoJ2FzY2lpJykp'),'','exec'))
print(f'  ') 

def getTiempesito():
    tiempesito = datetime.datetime.now().strftime('%H:%M:%S')
    return tiempesito
print(color.DARKCYAN + f"Versión: {vlocal}")
time.sleep(0.5)
print(Fore.MAGENTA + f"Buscando actualizaciones...")
print(Fore.MAGENTA + f"[{getTiempesito()}] Buscando actualizaciones...")
time.sleep(0.5)
vactualfix = vactual.text[:-1] #Muy cutre, lo se, yo soy cutre
if vactualfix != vlocal:
    print(Fore.BLACK + Back.YELLOW + f"[ADVERTENCIA] Nueva versión disponible: {vactualfix}")
    print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] Nueva versión disponible: {vactualfix}")
    print(Fore.GREEN + f"[¿?] ¿Deseas ver la lista de cambios? " + color.CYAN + "Si | No")
    vresp = input()
    if vresp.lower() == "si":
@@ -62,31 +65,20 @@ class color: #Tabla de colores (aunque tambíen uso colorama)
else:
    print(color.YELLOW + f"¡Tienes la última versión!")

def getTiempesito():
    tiempesito = datetime.datetime.now().strftime('%H:%M:%S')
    return tiempesito

fecha = datetime.datetime.now()
if fecha.year == 2020 and fecha.month == 4 and fecha.day > 25:
    print(Fore.BLACK + Back.RED + f"[{getTiempesito()}] [ERROR] Se acabo el tiempo de uso :(")
    bypass = input()
    if bypass != base64.b64decode("MTA4ZDljZmItMTFiNC00ZDkxLTgxZGUtYzBhZDU5NWQxNTg5".encode('ascii')).decode('ascii'):
        exit()

def cargarAjustes():
    try:
        with open('ajustes.json') as f:
            print(color.YELLOW + f'[{getTiempesito()}] Cargando \'ajustes.json\'...')
            time.sleep(5)
            global data 
            global data
            data = json.load(f)
            print(color.GREEN + f'[{getTiempesito()}] ¡Ajustes cargados con éxito!')
    except:
        print(Fore.BLACK + Back.RED + f"[ERROR] No se ha encontrado 'ajustes.json' en el directorio. ¿Que coño has hecho?")
        exit()
cargarAjustes()

if data['depurar'].lower() == 'true':
if data['depurar']:
    print(color.YELLOW + f'[{getTiempesito()}] La depuración esta activada.')
    logger = logging.getLogger('fortnitepy.xmpp')
    logger.setLevel(level=logging.DEBUG)
@@ -116,6 +108,37 @@ def store_detalles_autentificacion(email, details):
        json.dump(existing, fp, sort_keys=False, indent=4)

device_auth_details = get_detalles_autentificacion().get(data['correo'], {})
if data['sala_privacidad'].lower() == "publico":
    privasidad = fortnitepy.PartyPrivacy.PUBLIC
elif data['sala_privacidad'].lower() == "privado":
    privasidad = fortnitepy.PartyPrivacy.PRIVATE
elif data['sala_privacidad'].lower() == "amigos":
    privasidad = fortnitepy.PartyPrivacy.FRIENDS
elif data['sala_privacidad'].lower() == "amigosdeamigos":
    privasidad = fortnitepy.PartyPrivacy.FRIENDS_ALLOW_FRIENDS_OF_FRIENDS
else:
    privasidad = fortnitepy.PartyPrivacy.PUBLIC
    print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] {data['sala_privacidad']} no es una privacidad de sala válida.")
    print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] Se ha puesto la privacidad en PÚBLICO")
if data['plataforma'].lower() in ["win", "windows"]:
    plataforma = fortnitepy.Platform.WINDOWS
elif data['plataforma'].lower() in ["mac", "macintosh"]:
    plataforma = fortnitepy.Platform.MAC
elif data['plataforma'].lower() in ["psn", "playstation"]:
    plataforma = fortnitepy.Platform.PLAYSTATION
elif data['plataforma'].lower() in ["xb", "xbox"]:
    plataforma = fortnitepy.Platform.XBOX
elif data['plataforma'].lower() in ["ns", "switch"]:
    plataforma = fortnitepy.Platform.SWITCH
elif data['plataforma'].lower() == "ios":
    plataforma = fortnitepy.Platform.IOS
elif data['plataforma'].lower() in ["and", "android"]:
    plataforma = fortnitepy.Platform.ANDROID
else:
    plataforma = fortnitepy.Platform.SWITCH
    print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] {data['plataforma']} no es una plataforma válida.")
    print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] Se ha puesto la plataforma en SWITCH")
print(plataforma)
client = fortnitepy.Client(
    auth=fortnitepy.AdvancedAuth(
        email=data['correo'],
@@ -124,12 +147,14 @@ def store_detalles_autentificacion(email, details):
        delete_existing_device_auths=True,
        **device_auth_details
    ),
    status=base64.b64decode("aHR0cHM6Ly9naXRodWIuY29tL0xvbmRpdWgvTURKLWJvdA==".encode('ascii')).decode('ascii'),
    platform=fortnitepy.Platform.ANDROID,

    default_party_config={
        'privacy': fortnitepy.PartyPrivacy.PRIVATE,
    }
    status=data['estado'],
    platform=plataforma,
    default_party_config={'privacy': privasidad},
    default_party_member_config=[
        functools.partial(fortnitepy.ClientPartyMember.set_outfit, asset=data['skin_id']),
        functools.partial(fortnitepy.ClientPartyMember.set_backpack, data['mochila_id']),
        functools.partial(fortnitepy.ClientPartyMember.set_banner, icon=data['escudo'], color=data['escudo_color'], season_level=data['nivel_pase']),
    ]
)

@client.event
@@ -144,13 +169,13 @@ async def event_ready():

@client.event
async def event_party_invite(invite):
    if data['unirseinvitaciones'].lower() == 'true':
    if data['unirseinvitaciones']:
        try:
            await invite.accept()
            print(Fore.BLUE + f'[{getTiempesito()}] Se ha aceptado una invitación de sala de {invite.sender.display_name}')
        except Exception as e:
            pass
    if data['unirseinvitaciones'].lower() == 'false':
    else:
        if invite.sender.display_name in data['Admins']:
            await invite.accept()
            print(Fore.BLUE + f'[{getTiempesito()}] Se ha aceptado una invitación de sala de {invite.sender.display_name}')
@@ -162,10 +187,10 @@ async def event_party_invite(invite):

@client.event
async def event_friend_request(request):
    if data['aceptaramigos'].lower() == 'true':
    if data['aceptaramigos']:
        await request.accept()
        print(Fore.BLUE + f"[{getTiempesito()}] Se ha aceptado la petición de amistad de {request.display_name}")
    if data['aceptaramigos'].lower() == 'false':
    else:
        if request.display_name in data['Admins']:
            await request.accept()
            print(Fore.BLUE + f"[{getTiempesito()}] Se ha aceptado la petición de amistad de {request.display_name}")  
@@ -180,7 +205,7 @@ async def event_party_member_join(member):
    if client.user.display_name != member.display_name:
        print(Fore.BLUE + f"[{getTiempesito()}] {member.display_name} se ha unido a la sala.")
    time.sleep(1)
    await client.user.party.me.set_emote(asset='EID_Robot')
    await client.user.party.me.set_emote(asset=data['emote_id'])

@client.event
async def event_friend_message(message):
@@ -189,8 +214,63 @@ async def event_friend_message(message):
    split = args[1:]
    joinedArguments = " ".join(split)
    print('[' + getTiempesito() + '] {0.author.display_name}: {0.content}'.format(message))
    pre = data['prefijo'] #Para acortar

    if "/recargar" in args[0].lower():
    if pre + "privacidad" in args[0].lower():
        if message.author.display_name in data['Admins']:
            if len(args) != 2:
                await message.reply(f"Sintaxis del comando incorrecta")
                return
            else:
                if client.user.party.me.leader == True:
                    if args[1].lower() == "publico":
                        await client.user.party.set_privacy(fortnitepy.PartyPrivacy.PUBLIC)
                    elif args[1].lower() == "privado":
                        await client.user.party.set_privacy(fortnitepy.PartyPrivacy.PRIVATE)
                    elif args[1].lower() == "amigos":
                        await client.user.party.set_privacy(fortnitepy.PartyPrivacy.FRIENDS)
                    elif args[1].lower() == "amigosdeamigos":
                        await client.user.party.set_privacy(fortnitepy.PartyPrivacy.FRIENDS_ALLOW_FRIENDS_OF_FRIENDS)
                    else:
                        await message.reply("{args[1]} no es una privacidad de sala válida")
                        return
                    await message.reply("He cambiado la privacidad de esta sala a {args[1]}")
                else:
                    await message.reply("Necesito líder para cambiar la privacidad de la sala.")
        else:
            await message.reply('¡No tienes acceso a este comando!')

    if pre + "skin" in args[0].lower():
        if message.author.display_name in data['Admins']:
            if len(args) != 2:
                await message.reply(f"Sintaxis del comando incorrecta")
                return
            else:
                await client.user.party.me.set_outfit(asset=args[1])
        else:
            await message.reply('¡No tienes acceso a este comando!')

    if pre + "mochila" in args[0].lower():
        if message.author.display_name in data['Admins']:
            if len(args) != 2:
                await message.reply(f"Sintaxis del comando incorrecta")
                return
            else:
                await client.user.party.me.set_backpack(asset=args[1])
        else:
            await message.reply('¡No tienes acceso a este comando!')

    if pre + "emote" in args[0].lower():
        if message.author.display_name in data['Admins']:
            if len(args) != 2:
                await message.reply(f"Sintaxis del comando incorrecta")
                return
            else:
                await client.user.party.me.set_emote(asset=args[1])
        else:
            await message.reply('¡No tienes acceso a este comando!')

    if pre + "recargar" in args[0].lower():
        if message.author.display_name in data['Admins']:
            try:
                cargarAjustes()
@@ -202,14 +282,14 @@ async def event_friend_message(message):
            await message.reply('¡No tienes acceso a este comando!')


    if "/españa" in args[0].lower():
    if pre + "españa" in args[0].lower():
        await message.reply("¡Viva españa!")
        print(Fore.RED + "██████████████████████")
        print(Fore.YELLOW + "██████████████████████")
        print(Fore.RED + "██████████████████████")


    if "/gay" in args[0].lower():
    if pre + "gay" in args[0].lower():
        await message.reply("Yo tambíen soy gay :)")
        print(Fore.RED + "██████████████████████")
        print(Fore.YELLOW + "██████████████████████")
@@ -219,21 +299,21 @@ async def event_friend_message(message):
        print(color.PURPLE + "██████████████████████")


    if "/apagar" in args[0].lower():
    if pre + "apagar" in args[0].lower():
        if message.author.display_name in data['Admins']:
            await message.reply("¡Bot apagado!")
            exit()
        else:
            await message.reply('¡No tienes acceso a este comando!')


    if "/ayuda" in args[0].lower():
    if pre + "ayuda" in args[0].lower():
        if message.author.display_name in data['Admins']:
            await message.reply("Para obtener ayuda visita el apartado llamado \'Wiki\' en el repositorio de GitHub")
            await message.reply("Para obtener ayuda visita el apartado llamado \"Wiki\" en el repositorio de GitHub")
            await message.reply("https://github.com/Londiuh/MDJ-bot")


    if "/abandonar" in args[0].lower():
    if pre + "abandonar" in args[0].lower():
        if message.author.display_name in data['Admins']:
            await client.user.party.me.set_emote('EID_Snap')
            time.sleep(2)
@@ -245,11 +325,11 @@ async def event_friend_message(message):
                await message.reply(f"¡No tienes acceso a este comando!")


    if "/expulsar" in args[0].lower() and message.author.display_name in data['Admins']:
    if pre + "expulsar" in args[0].lower() and message.author.display_name in data['Admins']:
        user = await client.fetch_profile(joinedArguments)
        member = client.user.party.members.get(user.id)
        if member is None:
            await message.reply("No hay ningun usuario en la sala llamado" + args[1])
            await message.reply("No hay ningún usuario en la sala llamado" + args[1])
        else:
            try:
                await member.kick()
@@ -258,12 +338,12 @@ async def event_friend_message(message):
            except Exception as e:
                pass
                await message.reply(f"No puedo expulsar a {member.display_name}, no soy líder.")
                print(Fore.BLACK + Back.RED + f"[{getTiempesito()}] [ERROR] Error al expulsar a " + args[1] + f"porque no tengo líder." + Fore.WHITE)
                print(Fore.BLACK + Back.RED + f"[{getTiempesito()}] [ERROR] Error al expulsar a " + args[1] + f"porque no tengo líder.")
        if message.author.display_name not in data['Admins']:
            await message.reply(f"¡No tienes acceso a este comando!")


    if "/añadir" in args[0].lower() and message.author.display_name in data['Admins']:
    if pre + "añadir" in args[0].lower() and message.author.display_name in data['Admins']:
        user = await client.fetch_profile(joinedArguments)
        friends = client.friends
        if user is None:
@@ -285,7 +365,7 @@ async def event_friend_message(message):
            await message.reply(f"¡No tienes acceso a este comando!")


    if "/eliminar" in args[0].lower() and message.author.display_name in data['Admins']:
    if pre + "eliminar" in args[0].lower() and message.author.display_name in data['Admins']:
        user = await client.fetch_profile(joinedArguments)
        friends = client.friends
        if user is None:
@@ -307,7 +387,7 @@ async def event_friend_message(message):
            await message.reply(f"¡No tienes acceso a este comando!")


    if "/amigos" in args[0].lower() and message.author.display_name in data['Admins']:
    if pre + "amigos" in args[0].lower() and message.author.display_name in data['Admins']:
        friends = client.friends
        onlineFriends = []
        offlineFriends = []
@@ -332,7 +412,7 @@ async def event_friend_message(message):
            await message.reply(f"¡No tienes acceso a este comando!")


    if "/playlist-info" in args[0]:
    if pre + "playlist-info" in args[0]:
        await message.reply("PlaylistName: " + (client.user.party.playlist_info[0]))
        if message.author.display_name in data['Admins']:
            await message.reply("Tienes más información sobre la playlist en la consola :)")
@@ -344,7 +424,7 @@ async def event_friend_message(message):
            print(color.CYAN + f"<-------------[Playlist-Información]------------->")


    if "/lider" in args[0].lower() and message.author.display_name in data['Admins']:
    if pre + "lider" in args[0].lower() and message.author.display_name in data['Admins']:
        if len(args) != 1:
            user = await client.fetch_profile(joinedArguments)
            member = client.user.party.members.get(user.id)
@@ -366,13 +446,14 @@ async def event_friend_message(message):
            await message.reply(f"¡No tienes acceso a este comando!")


    if "/modo" in args[0].lower():
    if pre + "modo" in args[0].lower():
        if message.author.display_name in data['Admins']:
            if len(args) == 1:
                await message.reply(f"Sintaxis del comando incorrecta")
                return

            if "Playlist_" in args[1]:
                await client.user.party.me.set_ready(fortnitepy.ReadyState.NOT_READY)
                try:
                    await client.user.party.set_playlist(playlist="Playlist_PlaygroundV2")
                except:
@@ -385,59 +466,21 @@ async def event_friend_message(message):
                    res = await client.wait_for('friend_message')
                    content = res.content.lower()
                    if content == "si".lower():
                        await message.reply(f"¿Que clave de emparejemiento quieres que ponga? Responde no si no quieres clave o ya has puesto una")
                        await message.reply(f"¿Que clave de emparejemiento quieres que ponga? Responde \"no\" si no quieres clave o ya has puesto una")
                        res = await client.wait_for('friend_message')
                        content = res.content.lower()
                        if content != "no".lower():
                            await member.party.set_custom_key(content)
                            await message.reply(f"Clave puesta con exito.")
                            #await message.reply(f"Ten en cuenta que tienes que poder hacer privadas para comenzar la partida")
                            time.sleep(3)
                            await message.reply(f"Cambiando el modo de juego...")
                            time.sleep(3)
                        time.sleep(3)
                        await message.reply(f"Cambiando el modo de juego...")
                        time.sleep(3)
                        try:
                            await client.user.party.set_playlist(playlist=args[1])
                            time.sleep(1.3)
                            await client.user.party.me.set_ready(fortnitepy.ReadyState.SITTING_OUT)
                            time.sleep(7)
                            await message.reply(f"Si por alguna razón se ha quedado en 'Esperando emparegamiento...' tienes que crear una nueva sala")
                        except Exception as e:
                            pass
                            await message.reply(f"¡No puedo cambiar el modo si no soy líder!")
                            print(Fore.BLACK + Back.YELLOW + f"[{getTiempesito()}] [ADVERTENCIA] No se ha podido cambiar el modo porque el bot no es líder.")
                    else:
                        await message.reply(f"¡Todos los jugadores deben estar en listo!")
                else:
                    await message.reply(f"¡Todos los jugadores deben estar en listo!")
            elif "comida" in args[1]:
                try:
                    await client.user.party.set_playlist(playlist="Playlist_PlaygroundV2")
                except:
                    await message.reply(f"¡No puedes usar este comando si no soy líder!")
                    return
                user = await client.fetch_profile(message.author.display_name)
                member = client.user.party.members.get(user.id)
                if member.is_ready():
                    await message.reply(f"¿Estan todos los demás jugadores de la sala en listo? Si o no")
                    res = await client.wait_for('friend_message')
                    content = res.content.lower()
                    if content == "si".lower():
                        await message.reply(f"¿Que clave de emparejemiento quieres que ponga? Responde no si no quieres clave o ya has puesto una")
                        res = await client.wait_for('friend_message')
                        content = res.content.lower()
                        if content != "no".lower():
                            await member.party.set_custom_key(content)
                            await message.reply(f"Clave puesta con exito.")
                            #await message.reply(f"Ten en cuenta que tienes que poder hacer privadas para comenzar la partida")
                            time.sleep(3)
                            await message.reply(f"Cambiando el modo de juego...")
                            time.sleep(3)
                        try:
                            await client.user.party.set_playlist(playlist="Playlist_Barrier_16_B_Lava")
                            time.sleep(1.3)
                            await client.user.party.me.set_ready(fortnitepy.ReadyState.SITTING_OUT)
                            time.sleep(7)
                            await message.reply(f"Si por alguna razón se ha quedado en 'Esperando emparegamiento...' tienes que crear una nueva sala")
                            await message.reply(f"Si se ha quedado 'Esperando emparejamiento' usa \"{pre}modo reintentar\"")
                        except Exception as e:
                            pass
                            await message.reply(f"¡No puedo cambiar el modo si no soy líder!")
@@ -446,6 +489,12 @@ async def event_friend_message(message):
                        await message.reply(f"¡Todos los jugadores deben estar en listo!")
                else:
                    await message.reply(f"¡Todos los jugadores deben estar en listo!")
            elif "reintentar" in args[1]:
                await message.reply("Reintentando...")
                await client.user.party.me.set_ready(fortnitepy.ReadyState.NOT_READY)
                time.sleep(0.5)
                await client.user.party.me.set_ready(fortnitepy.ReadyState.SITTING_OUT)

            elif "gilipollas" in args[1].lower():
                await message.reply(f"Activando modo gilipollas...")
                time.sleep(1)
 38  
ajustes.json
@@ -1,15 +1,27 @@
{
    "correo": "",
    "contrasena": "",

    "aceptaramigos": "True",
    "unirseinvitaciones": "True",
	"depurar": "False",
    "Admins": [
		"ElLondiuh",
		"adminpersona2",
		"adminpersona3",
		"adminpersona4",
		"adminpersona5"
    ]
  "correo": "",
  "contrasena": "",

  "estado": "https://github.com/Londiuh/MDJ-bot",
  "sala_privacidad": "PUBLICO",
  "plataforma": "SWITCH",
  "nivel_pase": "777",

  "skin_id": "cid_npc_athena_commando_f_rebirthdefault_henchman",
  "mochila_id": "bid_481_graffitifuture",
  "emote_id": "eid_rocketrodeo",
  "escudo": "otherbanner23",
  "escudo_color": "defaultcolor12",

  "prefijo": "/",
  "aceptaramigos": true,
  "unirseinvitaciones": true,
	"depurar": false,
  "Admins": [
    "ElLondiuh",
    "adminpersona2",
    "adminpersona3",
    "adminpersona4",
    "adminpersona5"
  ]
}
 18  
cambios.md
@@ -1,2 +1,20 @@
###### Aviso: Las versiones de MDJ-BOT ya no se encuentran en "releases" ahora debes clonar el repositorio
[Clonar repositiorio](https://github.com/Londiuh/MDJ-bot/archive/master.zip)

## v1.2.0
- Mejoras
- Errores arreglados
- Correciónes ortograficas
- Nuevos comandos `/privacidad, /skin, /mochila, /emote`
- Nuevos ajustes (ahora puedes configurar muchas más cosas)
- He quitado el limite de tiempo (me descuide y no lo quite de la versión final)
- He quitado `/modo comida` (me olvide de quitarlo en la versión final, no funcionava)
- Archivo renombrado a **MDJ-BOT.py**
- Ahora puedes usar `/modo reintentar` si se quedo en **esperando emparejamiento...**
- Al usar `/modo <ID>` después de haver jugado un modo, el bot volvera a estar participando

## v1.0.1
- Errores arreglados

## v1.0.0
- Primera versión :smile:
