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





                            Thread _thread = new Thread(() =>
                            {
                                //Application.Run(new ŞifreDeğiştirme("ahmet.sekerci"));

                                ib = new InBoundEkranı(new TaskBilgileri { LoginID = "ahmet.sekerci" }, SantralRefID, inboundModel.AccountIDMatched, inboundModel.ANI, callTypeInbound);
                                ib.AccountAçMethodu = new InBoundEkranı.AccountAç(AccountAç);
                                //ib.Show();
                                Application.Run(ib);

                            });
                            _thread.SetApartmentState(ApartmentState.STA);
                            _thread.Start();









<div class="carousel slider" data-bs-ride="carousel" id="iskurslider">
            <ul class="carousel-indicators">
                <li class="active" data-bs-target="#iskurslider" data-bs-slide-to="0"></li>
                <li data-bs-target="#iskurslider" data-bs-slide-to="1"></li>
                <li data-bs-target="#iskurslider" data-bs-slide-to="2"></li>
                <li data-bs-target="#iskurslider" data-bs-slide-to="3"></li>
                <li data-bs-target="#iskurslider" data-bs-slide-to="4"></li>
            </ul>
            <div class="carousel-inner">
                <div class="carousel-item active">
                    <img src="images/slider1.png" class="w-100">
                    <div class="carousel-caption">
                        <h3>Süperman</h3>
                        <p>Şimdi Sinemalarda</p>
                        <a href="#" class="btn btn-primary">Detay</a>
                    </div>
                </div>
                <div class="carousel-item">
                    <img src="images/slider2.png" class="w-100">
                    <div class="carousel-caption d-none d-md-block">
                        <h2>AQUAMAN</h2>
                        <p>Çok Yakında Tüm Sinemalarda</p>
                        <a href="#" class="btn btn-warning">Devamını Oku...</a>
                    </div>

                </div>
                <div class="carousel-item">
                    <img src="images/slider3.png" class="w-100">
                    <div class="carousel-caption float-left">
                        <h2>Wonder Woman</h2>
                        <p>Çok Yakında Tüm Sinemalarda</p>
                        <a href="#" class="btn btn-danger">Devamını Oku...</a>
                    </div>
                </div>
                <div class="carousel-item">
                    <img src="images/slider4.png" class="w-100">
                    <div class="carousel-caption float-right text-dark">
                        <h2>Flas</h2>
                        <p>Çok Yakında Tüm Sinemalarda</p>
                        <a href="#" class="btn btn-dark">Devamını Oku...</a>
                    </div>
                </div>
                <div class="carousel-item">
                    <img src="images/slider5.png" class="w-100">
                    <div class="carousel-caption ip">
                        <h2>Flas</h2>
                        <p>Çok Yakında Tüm Sinemalarda</p>
                        <a href="#" class="btn btn-dark">Devamını Oku...</a>
                    </div>
                </div>
            </div>
            <a class="carousel-control-prev" href="#iskurslider" data-bs-slide="prev">
                <span class="carousel-control-prev-icon"></span>
            </a>
            <a class="carousel-control-next" href="#iskurslider" data-bs-slide="next">
                <span class="carousel-control-next-icon"></span>
            </a>
        </div>
