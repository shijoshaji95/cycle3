import java.io.*;
import java.net.*;
public class ClientThread implements Runnable
{
Socket socket = null;
BufferedReader readFromClient = null;
BufferedReader readFromServer = null;
PrintWriter writeToServer = null;
String message = null;
public ClientThread(Socket socket)
{
try
{
this.socket = socket;
readFromServer = new BufferedReader( new InputStreamReader( socket.getInputStream()));
writeToServer = new PrintWriter( socket.getOutputStream(), true);
readFromClient = new BufferedReader( new InputStreamReader(System.in));
new Thread(this).start();
while(true)
{
message = readFromClient.readLine();
writeToServer.println(message);
writeToServer.flush();
if(message.equalsIgnoreCase("exit"))
{
System.exit(0);
}
}
}
catch(IOException exp) { exp.printStackTrace();}
}
public void run()
{
try
{
while(true) {
String msg = readFromServer.readLine();
if(!msg.equalsIgnoreCase("exit"))
{
System.out.println(msg);
}
else { System.exit(0);}
}
}
catch(Exception exp)
{exp.printStackTrace();}
}
}
