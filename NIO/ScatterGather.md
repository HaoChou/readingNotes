# Scatter / Gather

scatter / gather经常用于需要将传输的数据分开处理的场合，例如传输一个由消息头和消息体组成的消息，你可能会将消息体和消息头分散到不同的buffer中，这样你可以方便的处理消息头和消息体。

## scatter 分散

scattering reads

        ByteBuffer header = ByteBuffer.allocate(128);
        ByteBuffer body   = ByteBuffer.allocate(1024);
        ByteBuffer[] bufferArray = { header, body };
        channel.read(bufferArray);

    
## gather 聚集

gathering writes

         ByteBuffer header = ByteBuffer.allocate(128);
         ByteBuffer body   = ByteBuffer.allocate(1024);
         //write data into buffers
         ByteBuffer[] bufferArray = { header, body };
         channel.write(bufferArray);


        