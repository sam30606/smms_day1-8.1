# 作業 - 8-1. 實作 Websocket 功能

Listen events
Emit 會回傳一樣的

## Run Command

```
sudo docker compose up
```

## events.gateway.ts

```
@WebSocketGateway(9090, {
  cors: {
    origin: '*',
  },
})
export class EventsGateway {
  @WebSocketServer()
  server: Server;

  @SubscribeMessage('events')
  findAll(@MessageBody() data: any): any {
    console.log(data);
    return { event: 'events', data: data };
  }
}

```

## events.module.ts

```
@Module({
  providers: [EventsGateway],
})
export class EventsModule {}

```
