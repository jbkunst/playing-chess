# Chess-db

This are scripts for parser pgns into a sqlite (tsv, RData) table!


## How to use

- Download a "chess database". For example you can download a big list of pgn from http://www.kingbase-chess.net/.
- Then run the R scripts.
- If you have a humble pc wait for 2-3 hours.
- And enjoy your chess database ;) in sqslite, Rdata, tsv format!



## Input

The input is a big list of pgn like this:

```
[Event "22. Abu Dhabi Masters"]
[Site "Abudhabi UAE"]
[Date "2015.08.31"]
[Round "9.38"]
[White "Ris, R"]
[Black "Raja, H"]
[Result "1-0"]
[WhiteElo "2449"]
[BlackElo "2247"]
[ECO "A13"]
[EventDate "2015.08.23"]

1.Nf3 Nf6 2.g3 d5 3.c4 e6 4.Bg2 c5 5.O-O Nc6 6.b3 d4 7.e3 Bd6 8.exd4 cxd4 
9.d3 h6 10.Re1 O-O 11.Ba3 e5 12.Bxd6 Qxd6 13.a3 a5 14.Ra2 Bf5 15.Nh4 Bh7 
16.Bh3 Nd7 17.Nf5 Bxf5 18.Bxf5 g6 19.Be4 f5 20.Bd5+ Kg7 21.Rae2 Rae8 22.
Qd2 Nc5 23.b4 axb4 24.axb4 Nd7 25.b5 Nb4 26.Bxb7 Nxd3 27.Qxd3 Nc5 28.Qa3 
Nxb7 29.Qxd6 Nxd6 30.Rxe5 Rxe5 31.Rxe5 Nxc4 32.Rc5 Re8 33.Kf1 Nb6 34.Nd2 
Na4 35.Rc4 Nb6 36.Rxd4 Re5 37.Rb4 Kf6 38.Rb1 Rd5 39.Nf3 g5 40.Rc1 Rxb5 41.
Rc6+ Kg7 42.Nd4 Rb1+ 43.Kg2 h5 44.Nxf5+ Kf7 45.Nd6+ Kg7 46.Ne4 Nd5 47.Nxg5
Rb2 48.Re6 h4 49.Re5 Nf6 50.Re7+ Kg6 51.Ne4 Ng4 52.h3 Ne3+ 53.Kf3 hxg3 54.
fxg3 Nd5 55.Rd7 Rb3+ 56.Kg4 Ne3+ 57.Kf4 Ng2+ 58.Ke5 Rb5+ 59.Rd5 Rxd5+ 60.
Kxd5 Kf5 61.Nd6+ Kg5 62.Ke4 Nh4 63.Ke3 Kh5 64.Ne4 Ng6 65.Kf3 Ne5+ 66.Kf4 
Ng6+ 67.Kf5 Ne7+ 68.Ke6 Ng6 69.Kf6 Nf8 70.Kf5 Ng6 71.g4+ Kh6 72.g5+ Kg7 
73.Nd6 Kh7 74.Nf7 Kg7 75.Ne5 Nh4+ 76.Kg4 Ng2 77.Nc4 Ne1 78.h4 Nd3 79.h5 
1-0
```

## Output

Is a table where every row is a pgn (a game), see a sample in `example_output.tsv`

```
event	site	date	round	white	black	result	whiteelo	blackelo	eco	moves	file_from
22. Abu Dhabi Masters	Abudhabi UAE	2015-08-31	9.38	Ris, R	Raja, H	1-0	2449	2247	A13	Nf3 Nf6 g3 d5 c4 e6 Bg2 c5 O-O Nc6 b3 d4 e3 Bd6 exd4 cxd4 d3 h6 Re1 O-O Ba3 e5 Bxd6 Qxd6 a3 a5 Ra2 Bf5 Nh4 Bh7 Bh3 Nd7 Nf5 Bxf5 Bxf5 g6 Be4 f5 Bd5+ Kg7 Rae2 Rae8 Qd2 Nc5 b4 axb4 axb4 Nd7 b5 Nb4 Bxb7 Nxd3 Qxd3 Nc5 Qa3 Nxb7 Qxd6 Nxd6 Rxe5 Rxe5 Rxe5 Nxc4 Rc5 Re8 Kf1 Nb6 Nd2 Na4 Rc4 Nb6 Rxd4 Re5 Rb4 Kf6 Rb1 Rd5 Nf3 g5 Rc1 Rxb5 Rc6+ Kg7 Nd4 Rb1+ Kg2 h5 Nxf5+ Kf7 Nd6+ Kg7 Ne4 Nd5 Nxg5 Rb2 Re6 h4 Re5 Nf6 Re7+ Kg6 Ne4 Ng4 h3 Ne3+ Kf3 hxg3 fxg3 Nd5 Rd7 Rb3+ Kg4 Ne3+ Kf4 Ng2+ Ke5 Rb5+ Rd5 Rxd5+ Kxd5 Kf5 Nd6+ Kg5 Ke4 Nh4 Ke3 Kh5 Ne4 Ng6 Kf3 Ne5+ Kf4 Ng6+ Kf5 Ne7+ Ke6 Ng6 Kf6 Nf8 Kf5 Ng6 g4+ Kh6 g5+ Kg7 Nd6 Kh7 Nf7 Kg7 Ne5 Nh4+ Kg4 Ng2 Nc4 Ne1 h4 Nd3 h5	A00-A39
80. ch-ESP 2015	Linares ESP	2015-08-31	9.14	Alsina Leal, Daniel	Navarro Lopez Menchero, D	1-0	2531	2213	A28	c4 e5 Nc3 Nc6 Nf3 Nf6 e4 Bc5 Nxe5 Nxe5 d4 Bb4 dxe5 Nxe4 Qf3 Bxc3+ bxc3 Ng5 Qg3 Ne6 f4 g6 f5 gxf5 Bd3 d5 Bxf5 dxc4 O-O Qe7 Be4 c6 a4 Bd7 Ba3 Qg5 Qf2 Qg7 h4 Rg8 Rab1 b6 a5 Nc5 Bxc5 bxc5 Qxc5 Qh6 Rb7	A00-A39
80. ch-ESP 2015	Linares ESP	2015-08-31	9.10	Alvarado Diaz, Alejandro	Fernandez Romero, Ernesto	1/2-1/2	2408	2488	A05	Nf3 Nf6 g3 b6 Bg2 Bb7 O-O g6 b3 Bg7 Bb2 O-O c4 d6 d4 e6 Nc3 Ne4 Qc2 Nxc3 Bxc3 f5 Ne1 Bxg2 Nxg2 e5 Rad1 exd4 Bxd4 Bxd4 Rxd4 Nc6 Rdd1 Qf6 Qd2 Ne5 Qd5+ Qf7 Nf4 Rae8 e3 a5 Kg2 Ng4 Rc1 Nf6 Qxf7+ Rxf7 Rfd1 g5 Nd5 Kf8 Nxf6 Rxf6 Rd4 h6 h4 Kg7 hxg5 hxg5	A00-A39
22. Abu Dhabi Masters	Abudhabi UAE	2015-08-31	9.3	Petrosian, TL	Jobava, Baadur	0-1	2623	2664	A24	Nf3 Nf6 g3 g6 Bg2 Bg7 O-O O-O c4 d6 Nc3 e5 d3 c6 Bg5 Be6 Rb1 Nbd7 Nd2 a5 a3 h6 Bxf6 Nxf6 b4 axb4 axb4 d5 Qc2 Qe7 Rfc1 h5 b5 h4 bxc6 bxc6 Rb6 Rfc8 Rcb1 hxg3 hxg3 Ng4 e3 e4 dxe4 d4 Nd1 dxe3 Nxe3 Nxe3 fxe3 Be5 Nf1 Qc5 R6b4 Kg7 Qf2 Ra3 Rb7 Qxc4 R1b4 Qa2 Qf3 Ra7 g4 c5 R4b6 Rxb7 Rxb7 c4 g5 c3 Rb5 c2	A00-A39
22. Abu Dhabi Masters	Abudhabi UAE	2015-08-31	9.16	Gabuzyan, Hovhannes	Vaibhav, S	0-1	2593	2552	A22	c4 e5 g3 Nf6 Bg2 d5 cxd5 Nxd5 Nc3 Nb6 d3 Be7 Be3 O-O Rc1 Re8 Qd2 Bf8 Nf3 Nc6 O-O Nd4 Bxd4 exd4 Nb5 c5 b4 Bd7 bxc5 Bxb5 cxb6 axb6 Qf4 Bd6 Qxd4 Rxe2 Qg4 Bd7 Qh5 g6 Qh6 Ra5 Rb1 Rh5 Qc1 Rxa2 d4 b5 Re1 Qf6 Ra1 Rxa1 Qxa1 Bc6 Ne5 Bxg2 Kxg2 Qe6 h4 Kg7 Kg1 Qd5 Ng4 b4 Re8 Qf3 Nh2 Qa3 Ra8 Qxa1+ Rxa1 Rb5 Rb1 Kf6 Kf1 Ke6 Ng4 Kd5 Rd1 Kc4 Ne3+ Kc3 Rc1+ Kxd4 Ke2 b3 f4 Rb4 Rd1+ Kc5 Rc1+ Kd4 Rd1+ Kc5 Rc1+ Kb5 Rb1 Bc5 Nd1 Bd4 Kd3 b2 Kc2 Kc4	A00-A39
80. ch-ESP 2015	Linares ESP	2015-08-31	9.32	Cuenca Jimenez, Francisco Javier	Jimenez Villena, Fco Jose	0-1	2210	2116	A21	c4 f5 g3 Nf6 Bg2 e5 Nc3 Bc5 d3 O-O e3 c6 Nge2 d6 O-O a5 a3 Nbd7 Rb1 Bb6 b4 axb4 axb4 Kh8 d4 Bc7 Qc2 e4 Nf4 Qe8 h4 h6 Bb2 g5 hxg5 hxg5 Nh3 Qh5 Qe2 Qh6 Ra1 Rb8 c5 d5 b5 Rf7 b6 Bd8 Rfb1 Nf8 Bc1 N6h7 Kf1 f4 exf4 Bxh3 fxg5 Nxg5 Bxg5 Bxg5 Bxh3 Qxh3+ Ke1 Ne6 Rb4 Rbf8 Nd1 e3 Nxe3 Bxe3 Qxe3 Qh1+ Ke2 Rxf2+	A00-A39
22. Abu Dhabi Masters	Abudhabi UAE	2015-08-31	9.17	Romanov, E	Harika, Dronavalli	1/2-1/2	2586	2509	A05	Nf3 Nf6 b3 g6 Bb2 Bg7 g3 b6 Bg2 Bb7 O-O O-O a4 c5 a5 d5 c4 Na6 Na3 Nb4 Nc2 bxa5 cxd5 Bxd5 Ne3 Ng4 Nc4 Bxb2 Nxb2 Rb8 Nc4 Nc6 d3 Nf6 Ra3 Rb5 Ne3 Bxf3 Bxf3 Nd4 Bg2 Qc7 Nc4 Rfb8 e3 Nxb3 Qc2 Rb4 Qa2 a4 Rxa4 Rxa4 Qxa4 Qd7 Bc6 Qxd3 Qxa7 Rf8 Qxe7 Qxc4 Qxf6 Qd3 h4 h5 g4 Rd8 Bb5 Qd6 Qxd6 Rxd6 gxh5 gxh5 Kh2 Nd2 Rc1 Rf6 Rxc5 Rxf2+ Kg1 Rf3 Re5 Rh3 Rd5 Ne4 Rxh5	A00-A39
3. China Mind Team	Zaozhuang CHN	2015-08-31	6.6	Li, Chao2	Wang Hao	1/2-1/2	2748	2705	A22	c4 e5 Nc3 Nf6 g3 Bb4 Bg2 O-O e4 Bxc3 bxc3 c6 Ne2 d5 cxd5 cxd5 exd5 Nxd5 O-O Nc6 Rb1 Nb6 d4 Be6 a4 Bd5 Rb5 Bxg2 Kxg2 a6 Rc5 Nd7 Rd5 Ne7 Rd6 Nc8 Rd5 Ncb6 Rd6 Nc4 Rd5 Qc7 dxe5 Qc6 f3 Ndxe5 Nf4 Rfe8 Re1 h6 h4 Ng6 Rxe8+ Rxe8 Nxg6 Qxg6 Rd8 Rxd8 Qxd8+ Kh7 Qd5	A00-A39
3. China Mind Team	Zaozhuang CHN	2015-08-31	6.11	Wen Yang	Lan, Zilun	1-0	2618	2241	A39	Nf3 Nf6 g3 c5 Bg2 Nc6 c4 g6 d4 cxd4 Nxd4 Bg7 O-O O-O Nc3 Nxd4 Qxd4 d6 Qd3 Qa5 h3 Be6 Bd2 Qc7 b3 a6 Rac1 Rab8 Kh2 Rfd8 e4 Qd7 f4 Qe8 a4 Bd7 Rfe1 b5 cxb5 axb5 a5 e5 b4 exf4 Bxf4 Nh5 Be3 Qe5 Bf2 Rbc8 Nd5 Kh8 Qd2 Nf6 Nxf6 Bxf6 Rxc8 Rxc8 Rc1 Rc4 a6 Bc6 a7 Ba8 Rd1 Rc6 Qa2 Kg7 Bd4 Qe7 e5 dxe5 Bxc6 Bxc6 Bc5 Qe8 Rd6 Ba8 Rb6 Bd8 Rb8 Qc6 Rxa8 Qxa8 Qg2 e4 Qd2 Bc7 Qd4+ Kh6 Bf8+ Kh5 Qc5+ g5 Qf5	A00-A39
3. China Mind Team	Zaozhuang CHN	2015-08-31	5.2	Wang Chen	Xu Jun	1/2-1/2	2524	2526	A01	b3 d5 Bb2 c5 e3 a6 Nf3 Nc6 g3 Nf6 Bg2 g6 Ne5 Nxe5 Bxe5 Bg7 O-O O-O d4 Qa5 dxc5 Qxc5 Nc3 Bg4 Qd2 Rac8 Rac1 Ne4 Nxe4 dxe4 Bxg7 Kxg7 c4 Bf3 Bxf3 exf3 e4 Qh5 Qc3+ Kg8 Rfe1 Rfd8 Re3 b5 Rxf3 bxc4 Kg2 Qg4 Qe5 Rd3 Rf4 Qd7 Rxc4 Rxc4 bxc4 Rd4 c5 Rc4 Qb8+ Kg7 Qb3 Qb5 Qxb5 axb5 Rf3	A00-A39

```

