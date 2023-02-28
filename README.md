# MERN
Backend Node.js and Frontend React sample project for learning

UDP server =>

using System.Net;
using System.Net.Sockets;
using System.Text;
using System.Text.RegularExpressions;

namespace UDP_Server;
class Program
{
    private const int port = 5000;



    private static void receiveMessage(UdpClient listener, IPEndPoint groupEP)
    {
        try
        {

            byte[] bytes = listener.Receive(ref groupEP);

            Console.WriteLine($" {Encoding.ASCII.GetString(bytes, 0, bytes.Length)}");


        }
        catch (SocketException ex)
        {
            Console.WriteLine(ex.Message);
        }
    }


    static void Main(string[] args)
    {
        UdpClient listener = new UdpClient(port);
        IPEndPoint groupEP = new IPEndPoint(IPAddress.Any, port);

        while (true)
        {

            receiveMessage(listener, groupEP);
        }
    }

}


UDP client => 


using System.Net;
using System.Net.Sockets;
using System.Text;

namespace UDP_Client;
class Program
{


    static void Main(string[] args)
    {

        Socket s = new Socket(AddressFamily.InterNetwork, SocketType.Dgram, ProtocolType.Udp);

        IPAddress broadcast = IPAddress.Parse("127.0.0.1");
        Console.WriteLine("Enter message to sent to broadcast address");

        var message = Console.ReadLine();
        while (message != string.Empty)
        {
            byte[] sendbuf = Encoding.ASCII.GetBytes(message);
            IPEndPoint ep = new IPEndPoint(broadcast, 5000);

            s.SendTo(sendbuf, ep);
            Console.WriteLine("Message sent to the broadcast address");

            message = Console.ReadLine();
        }

        Console.ReadLine();

    }

}


