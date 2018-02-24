<[Go to homepage](https://ryozuki.github.io/discord.aio/docs)>

## Events
- [on_ready](#event-on_ready)
- [on_channel_create](#event-on_channel_create)
- [on_channel_update](#event-on_channel_update)
- [on_channel_delete](#event-on_channel_delete)
- [on_guild_create](#event-on_guild_create)
- [on_guild_delete](#event-on_guild_delete)
- [on_ban](#event-on_ban)
- [on_ban_remove](#event-on_ban_remove)
- [on_typing_start](#event-on_typing_start)
- [on_message](#event-on_message)
- [on_message_update](#event-on_message_update)
- [on_message_delete_bulk](#event-on_message_delete_bulk)
- [on_message_reaction_add](#event-on_message_reaction_add)
- [on_message_reaction_remove](#event-on_message_reaction_remove)
- [on_message_reaction_remove_all](#event-on_message_reaction_remove_all)

### Event: on_ready
Raised when:
- The client is ready and connected.

```python
@bot.event()
async def on_ready():
    print('Connected!')
    print(f'My username is {bot.user}')
```

### Event: on_channel_create
Raised when:
- A new channel is created

Event Parameters:
- `channel`: The created channel

### Event: on_channel_update
Raised when:
- A channel is updated

Event Parameters:
- `channel`: The updated channel

### Event: on_channel_delete
Raised when:
- A channel is deleted

Event Parameters:
- `channel`: The deleted channel

### Event: on_channel_pin
Raised when:
- A message is pinned or unpinned in a text channel.

*Note: This is not raised when a pinned message is deleted.*

Event Parameters:
- `channel_id`: The id of the channel
- `last_pin_timestamp`: The time at which the most recent pinned message was pinned

### Event: on_guild_create
Raised when:
- After the `on_ready` event, to fullfill the guild information.
- When a Guild becomes available again to the client.
- When the current user joins a new Guild.

Event Parameters:
- `guild`: The guild

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
- `guild`: The guild

```python
@bot.event()
async def on_guild_delete(guild):
    print(f'{guild.name} went offline?')
    if not guild.unavailable:
        print(f'I got removed from {guild}!')
```

### Event: on_ban
Raised when:
- A user is banned from a guild

Event Parameters:
- `guild_id`: The guild id
- `user`: The banned 

### Event: on_ban_remove
Raised when:
- A user is unbanned from a guild

Event Parameters:
- `guild_id`: The guild id
- `user`: The unbanned user

### Event: on_typing_start
Raised when:
- A user starts typing in a channel

Event Parameters:
- `user_id`: The id of the user that started typing.
- `channel_id`: The id of the channel where the action happened.
- `timestamp`: The timestamp telling when it happened.

```python
@bot.event()
async def on_typing_start(user_id, channel_id, timestamp):
    user = await bot.get_user(user_id)
    print(f'{user} started typing!')
```

### Event: on_message
Raised when:
- A user send a message to a channel

Event Parameters:
- `user_id`: The id of the user that started typing.
- `channel_id`: The id of the channel where the action happened.
- `timestamp`: The timestamp telling when it happened.

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
- `message`: The Channel message that has been updated

```python
@bot.event()
async def on_message_create(message):
    print(f'A message with id {message.id} has been updated.')
```

### Event: on_message_delete
Raised when:
- A message is deleted.

Event Parameters:
- `id`: The id of the message
- `channel_id`: The id of the channel

```python
@bot.event()
async def on_message_delete(id, channel_id):
    print(f'A message with id {id} has been deleted.')
```

### Event: on_message_delete_bulk
Raised when:
- Multiple messages are deleted at once.

Event Parameters:
- `ids`: The ids of the messages
- `channel_id`: The id of the channel

```python
@bot.event()
async def on_message_delete_bulk(ids, channel_id):
    print(f'Multiple messages have been deleted')
```

### Event: on_message_reaction_add
Raised when:
- A user adds a reaction to a message

Event Parameters:
- `user_id`: The id of the user
- `channel_id`: The id of the channel
- `message_id`: The id of the message
- `emoji`: The emoji used to react

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
- `user_id`: The id of the user
- `channel_id`: The id of the channel
- `message_id`: The id of the message
- `emoji`: The emoji used to react

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
- `channel_id`: The id of the channel
- `message_id`: The id of the message