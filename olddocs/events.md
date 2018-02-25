\<[Go to homepage](https://ryozuki.github.io/discord.aio/docs)>

## Events
- [on_ready](#event-on_ready)
- [on_resumed](#event-on_resumed)
- [on_invalid_session](#event-on_invalid_session)
- [on_channel_create](#event-on_channel_create)
- [on_channel_update](#event-on_channel_update)
- [on_channel_delete](#event-on_channel_delete)
- [on_guild_create](#event-on_guild_create)
- [on_guild_delete](#event-on_guild_delete)
- [on_guild_emojis_update](#event-on_guild_emojis_update)
- [on_guild_integrations_update](#event-on_guild_integrations_update)
- [on_guild_member_add](#event-on_guild_member_add)
- [on_guild_member_remove](#event-on_guild_member_remove)
- [on_guild_member_update](#event-on_guild_member_update)
- [on_guild_members_chunk](#event-on_guild_members_chunk)
- [on_guild_role_create](#event-on_guild_role_create)
- [on_guild_role_update](#event-on_guild_role_update)
- [on_guild_role_delete](#event-on_guild_role_delete)
- [on_ban](#event-on_ban)
- [on_ban_remove](#event-on_ban_remove)
- [on_message](#event-on_message)
- [on_message_update](#event-on_message_update)
- [on_message_delete_bulk](#event-on_message_delete_bulk)
- [on_message_reaction_add](#event-on_message_reaction_add)
- [on_message_reaction_remove](#event-on_message_reaction_remove)
- [on_message_reaction_remove_all](#event-on_message_reaction_remove_all)
- [on_presence_update](#event-on_presence_update)
- [on_typing_start](#event-on_typing_start)
- [on_user_update](#event-on_user_update)
- [on_voice_state_update](#event-on_voice_state_update)
- [on_voice_server_update](#event-on_voice_server_update)
- [on_webhooks_update](#event-on_webhooks_update)

### Event: on_ready
Raised when:
- The client is ready and connected.

*Note: Before this event is raised, DiscordBot.user is filled with information.*

```python
@bot.event()
async def on_ready():
    print('Connected!')
    print(f'My username is {bot.user}')
```

### Event: on_resumed
Raised when:
- A client has sent a resume payload to the gateway (for resuming existing sessions).

### Event: on_invalid_session
Raised when:
- The gateway could not initialize a session after receiving an Opcode 2 Identify
- The gateway could not resume a previous session after receiving an Opcode 6 Resume
- The gateway has invalidated an active session and is requesting client action

Event Parameters:
- `resume`  (**bool**): Indicates whether the client can resume.

### Event: on_channel_create
Raised when:
- A new channel is created

Event Parameters:
- `channel`     (**Channel**): The created channel

### Event: on_channel_update
Raised when:
- A channel is updated

Event Parameters:
- `channel`     (**Channel**): The updated channel

### Event: on_channel_delete
Raised when:
- A channel is deleted

Event Parameters:
- `channel`     (**Channel**): The deleted channel

### Event: on_channel_pin
Raised when:
- A message is pinned or unpinned in a text channel.

*Note: This is not raised when a pinned message is deleted.*

Event Parameters:
- `channel_id`          (**int**): The id of the channel
- `last_pin_timestamp`  (**int**): The time at which the most recent pinned message was pinned

### Event: on_guild_create
Raised when:
- After the `on_ready` event, to fullfill the guild information.
- When a Guild becomes available again to the client.
- When the current user joins a new Guild.

Event Parameters:
- `guild`       (**Guild**): The guild

```python
@bot.event()
async def on_guild_create(guild):
    print(f'I\'m connected to {guild.name} guild, it got {len(guild.channels)} channels.')
```

### Event: on_guild_delete
Raised when:
- A guild becomes unavailable during a guild outage
- The user leaves or is removed from a guild
- When the current user joins a new Guild.

*Note: If the unavailable attribute is not set, the user was removed from the guild.*

Event Parameters:
- `guild`       (**Guild**): The guild

```python
@bot.event()
async def on_guild_delete(guild):
    print(f'{guild.name} went offline?')
    if not guild.unavailable:
        print(f'I got removed from {guild}!')
```

### Event: on_guild_emojis_update
Raised when:
- When a guild's emojis have been updated.

Event Parameters:
- `guild_id`    (**int**): The guild id
- `emojis`      (**list**): A list of emojis

### Event: on_guild_integrations_update
Raised when:
- When a guild integration is updated.

Event Parameters:
- `guild_id`    (**int**): The guild id.

### Event: on_guild_member_add
Raised when:
- When a new user joins a guild.

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `member`      (**GuildMember**): The user that joined.

### Event: on_guild_member_remove
Raised when:
- A user is removed from a guild (leave/kick/ban).

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `user`        (**User**): The user that was removed/left.

### Event: on_guild_member_update
Raised when:
- A guild member is updated

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `roles`       (**list**): User role ids.
- `user`        (**User**): The user.
- `nick`        (**str**): Nickname of the user in the guild.

### Event: on_guild_members_chunk
Raised when:
- In response to Guild Request Members.

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `members`       (**list**): Set of guild members

### Event: on_guild_role_create
Raised when:
- A guild role is created.

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `role`       (**Role**): The role created

### Event: on_guild_role_update
Raised when:
- A guild role is updated.

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `role`       (**Role**): The role updated

### Event: on_guild_role_delete
Raised when:
- A guild role is deleted.

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `role_id`       (**int**): The id of the deleted role

### Event: on_ban
Raised when:
- A user is banned from a guild

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `user`        (**User**): The banned .

### Event: on_ban_remove
Raised when:
- A user is unbanned from a guild

Event Parameters:
- `guild_id`    (**int**): The guild id.
- `user`        (**User**): The unbanned user.

### Event: on_message
Raised when:
- A user send a message to a channel

Event Parameters:
- `user_id`     (**int**): The id of the user that started typing.
- `channel_id`  (**int**): The id of the channel where the action happened.
- `timestamp`   (**int**): The timestamp telling when it happened.

```python
@bot.event()
async def on_message(message):
    print(f'{message.author}: {message.content}')
```

### Event: on_message_update
Raised when:
- A message is updated.

*Note: Unlike creates, message updates may contain only a subset of the full message object payload (but will always contain an id and channel_id)*

Event Parameters:
- `message` (**ChannelMessage**): The Channel message that has been updated

```python
@bot.event()
async def on_message_create(message):
    print(f'A message with id {message.id} has been updated.')
```

### Event: on_message_delete
Raised when:
- A message is deleted.

Event Parameters:
- `id`          (**int**): The id of the message.
- `channel_id`  (**int**): The id of the channel.

```python
@bot.event()
async def on_message_delete(id, channel_id):
    print(f'A message with id {id} has been deleted.')
```

### Event: on_message_delete_bulk
Raised when:
- Multiple messages are deleted at once.

Event Parameters:
- `ids`         (**int**): The ids of the messages
- `channel_id`  (**int**): The id of the channel

```python
@bot.event()
async def on_message_delete_bulk(ids, channel_id):
    print(f'Multiple messages have been deleted')
```

### Event: on_message_reaction_add
Raised when:
- A user adds a reaction to a message

Event Parameters:
- `user_id`     (**int**): The id of the user
- `channel_id`  (**int**): The id of the channel
- `message_id`  (**int**): The id of the message
- `emoji`       (**Emoji**): The emoji used to react

```python
@bot.event()
async def on_message_reaction_add(user_id, channel_id, message_id, emoji):
    user = await bot.get_user(user_id)
    print(f'{user} reacted to a message with {emoji.name}')
```

### Event: on_message_reaction_remove
Raised when:
- A user removes a reaction from a message

Event Parameters:
- `user_id`     (**int**): The id of the user
- `channel_id`  (**int**): The id of the channel
- `message_id`  (**int**): The id of the message
- `emoji`       (**Emoji**): The emoji used to react

```python
@bot.event()
async def on_message_reaction_add(user_id, channel_id, message_id, emoji):
    user = await bot.get_user(user_id)
    print(f'{user} removed reaction {emoji.name} from a message.')
```

### Event: on_message_reaction_remove_all
Raised when:
- A user explicitly removes all reactions from a message.

Event Parameters:
- `channel_id`  (**int**): The id of the channel
- `message_id`  (**int**): The id of the message

### Event: on_presence_update
Raised when:
- A user's presence is updated for a guild.

*Note: The user object within this event can be partial, the only field which must be set is the id field*

Event Parameters:
- `user`  (**User**): The user presence is being updated for
- `roles`  (**list**): Ids of the roles this user is in
- `game`  (**?Activity**): Null, or the user's current activity
- `guild_id`  (**int**): The guild id
- `status`  (**str**): Either "idle", "dnd", "online", or "offline"

### Event: on_typing_start
Raised when:
- A user starts typing in a channel

Event Parameters:
- `user_id`     (**int**): The id of the user that started typing.
- `channel_id`  (**int**): The id of the channel where the action happened.
- `timestamp`   (**int**): The timestamp telling when it happened.

```python
@bot.event()
async def on_typing_start(user_id, channel_id, timestamp):
    user = await bot.get_user(user_id)
    print(f'{user} started typing!')
```

### Event: on_user_update
Raised when:
- Properties about the user change

Event Parameters:
- `user`     (**User**): The user that has been updated

### Event: on_voice_state_update
Raised when:
- Someone joins/leaves/moves voice channels.

Event Parameters:
- `voice_state`     (**VoiceState**): The voice state object

### Event: on_voice_server_update
Raised when:
- A guild's voice server is updated.
- This is sent when initially connecting to voice, and when the current voice instance fails over to a new server.

Event Parameters:
- `token`	        (**str**): Voice connection token-
- `guild_id`        (**int**): The guild this voice server update is for
- `endpoint`        (**str**): The voice server host

### Event: on_webhooks_update
Raised when:
- A guild's voice server is updated.
- This is sent when initially connecting to voice, and when the current voice instance fails over to a new server.

Event Parameters:
- `guild_id`        (**int**): Id of the guild
- `channel_id`      (**int**): Id of the channel