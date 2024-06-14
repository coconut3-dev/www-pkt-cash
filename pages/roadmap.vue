<template>
  <div class="v-roadmap">
    <section class="v-header-section">
      <SpotAInternal title="Roadmap" />
    </section>
    <section class="v-tabs-nav">
      <vue-tabs centered active-tab-color="transparent">
        <v-tab title="Introduction">
          <div class="container">
            <div class="v-introduction__inner">
              <div class="v-introduction__inner_left">
                <h2>Introduction</h2>
              </div>
              <div class="v-introduction__inner_right">
                <p>The PKT roadmap is an overview of the PKT ecosystem development. It is separated into four phases: Launch, Utility, Scale, and Innovate. Each phase defines an era of focus. This provides a guide for community developers and contributors regarding what tools, functionality and capabilities are integral to each era.</p>
                <p>While the phases of the roadmap are presented in order, contributors are working concurrently across multiple eras. This nonlinear development invites a wide range of community participation. While many projects cannot be developed in sequence, considering certain dependencies, this development style matches the project’s agile, open source ethos.</p>
                <p>As you explore this roadmap, you will see the years of development effort that are represented across each phase. Each milestone is a community achievement. Each accomplishment moves the project towards its mission of decentralizing internet access and getting the next billion people online. Since PKT has no central infrastructure, no company, no foundation, no DAO, and no bank account, this roadmap represents a collective vision that honors the global PKT community’s time, intelligence and gracious contributions.</p>
              </div>
            </div>
            <div class="v-introduction__papers">
              <div class="v-introduction__papers_single yellow_bg">
                <p>PacketCrypt</p>
                <h4>Yellow Paper</h4>
                <a href="https://pkt.cash/PacketCrypt-2020-09-04.pdf" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>Read now</span></a>
              </div>
              <div class="v-introduction__papers_single white_bg">
                <p>PKT Network</p>
                <h4>White Paper</h4>
                <a href="https://pkt.cash/PKT_Network_v1.0_2021.02.01.pdf" target="_blank" class="c-common-button c-common-button__bordered c-common-button__dark_blue"><span>Read now</span></a>
              </div>
            </div>
            <div class="v-introduction__chess">
              <BlocksChessCommon :list="chess_list" />
            </div>
          </div>
        </v-tab>

        <v-tab title="Phases">
          <div class="v-phases__inner">
            <div class="container">
              <template>
                <div class="v-phases__inner__navigation">
                  <template v-for="item of phases_list">
                    <div class="c-phase" v-on:click="phase = item.title" :id="item.title">
                      <h4 class="c-phase__title">{{ item.title }}</h4>
                      <img :src="item.img_url" :alt="item.title" class="c-phase__img" />
                      <p class="c-phase__number">{{ item.number }}</p>
                    </div>
                  </template>
                </div>
              </template>
              <div class="v-phases__inner__content">
                <template v-if="phase === item.title" v-for="item of phases_content">
                  <div class="v-phases__inner__content__main">
                    <div class="v-phases__inner__content__main_left">
                      <h3>{{ item.number }}<br />{{ item.title }}</h3>
                    </div>
                    <div class="v-phases__inner__content__main_right">
                      <p>{{ item.description }}</p>
                      <p v-if="item.description_2">{{ item.description_2 }}</p>
                      <p v-if="item.description_3">{{ item.description_3 }}</p>
                      <p v-if="item.description_4">{{ item.description_4 }}</p>
                      <p v-if="item.description_5">{{ item.description_5 }}</p>
                    </div>
                  </div>
                  <template v-if="item.pr_completed">
                    <div class="v-phases__inner__content__analytics">
                      <div class="container">
                        <div class="v-phases__inner__content__analytics_data orange_bg">
                          <p class="v-phases__inner__content__analytics_data__value">{{ item.pr_completed }}</p>
                          <hr />
                          <h3 class="v-phases__inner__content__analytics_data__title">{{ item.title_1 }}</h3>
                        </div>
                        <div class="v-phases__inner__content__analytics_data blue_bg">
                          <p class="v-phases__inner__content__analytics_data__value">{{ item.months_completion }}</p>
                          <hr />
                          <h3 class="v-phases__inner__content__analytics_data__title">{{ item.title_2 }}</h3>
                        </div>
                        <div class="v-phases__inner__content__analytics_data green_bg">
                          <p class="v-phases__inner__content__analytics_data__value">{{ item.decimations }}</p>
                          <hr />
                          <h3 class="v-phases__inner__content__analytics_data__title">{{ item.title_3 }}</h3>
                        </div>
                      </div>
                    </div>
                  </template>
                  <template v-if="item.work_scope === true">
                    <div class="v-phases__inner__content__scope">
                      <h3>Work Scope</h3>
                      <template v-for="project of item.work_scope_items">
                        <div class="v-phases__inner__content__scope_single">
                          <div class="v-phases__inner__content__scope_single_list"><img :src="project.icon" :alt="project.title" v-if="project.icon" /></div>
                          <div class="v-phases__inner__content__scope_single_text">
                            <h5>{{ project.title }}</h5>
                            <p>{{ project.descr }} <span v-if="project.descr_2">{{ project.descr_2 }}</span></p>
                          </div>
                        </div>
                      </template>
                    </div>
                  </template>
                </template>
              </div>
            </div>
          </div>
        </v-tab>
      </vue-tabs>
    </section>
  </div>
</template>

<script>
import SpotAInternal from "~/components/Common/SpotAInternal";
import {VueTabs, VTab} from "vue-nav-tabs";
import "vue-nav-tabs/themes/vue-tabs.css";
import BlocksChessCommon from "~/components/Common/BlocksChessCommon";
export default {
  components: {
    SpotAInternal,
    VueTabs,
    VTab,
    BlocksChessCommon
  },
  data() {
    return {
      phase: 'Launch',
      chess_list: [
        {
          text_direction: "text_left",
          single_title: "Origin Story",
          single_descr: "PKT was born out of the cjdns mesh networking project, which launched in 2011. PKT lead dev, and cjdns inventor, Caleb James DeLisle realized the cjdns network would struggle to scale without a financial incentive. After developing PacketCrypt, on August 19, 2019, Caleb launched the PKT blockchain. This marked a new era of public incentive to setup and maintain mesh infrastructure.",
          single_url: "/cjdns",
          single_link: "Learn more",
          external: false,
          single_img: "/img/roadmap-introduction-origib-story.webp",
        },
        {
          text_direction: "text_right",
          single_title: "Cjdns: Routing Protocol",
          single_descr: "Cjdns's uses a novel routing protocol called compact source routing. Compact source routing enhances data  efficiency by including the directions across the network, instead of the IP address of the destination. This approach optimizes network performance and facilitates faster and more secure communication across the mesh network.",
          single_url: "/cjdns",
          external: false,
          single_link: "Learn more",
          single_img: "/img/roadmap-introduction-cjdns.webp",
        }
      ],
      phases_list: [
        {
          title: "Launch",
          img_url: "/img/roadmap-icon-launch.webp",
          number: "01"
        },
        {
          title: "Utility",
          img_url: "/img/roadmap-icon-utility.webp",
          number: "02"
        },
        {
          title: "Scale",
          img_url: "/img/roadmap-icon-scale.webp",
          number: "03"
        },
        {
          title: "Innovate",
          img_url: "/img/roadmap-icon-innovate.webp",
          number: "04"
        },
      ],
      phases_content: [
        {
          number: "01",
          title: "Launch",
          description: "PKT evolved from the cjdns mesh networking project, which was created by Caleb James DeLisle circa 2011. With the emergence of Bitcoin’s Lightning Network in 2016, Caleb realized it could be possible to process microtransaction payments for bandwidth. Caleb created the PacketCrypt proof-of-work in 2019, and launched the PKT blockchain mainnet on August 20, 2019 (Paris Time).",
          description_2: "The Launch era focused on establishing PKT’s decentralized infrastructure. This included unifying around PacketCrypt’s bandwidth-hard mining algorithm and fostering community growth. Major developments during this era included multiple PKT wallets, the PKT block explorer, the PKT.Cash website, OTC trading app, and funding the first projects via the Network Steward.",
          title_1: "Projects Completed",
          title_2: "Months of Phase",
          title_3: "Decimations",
          pr_completed: "15",
          months_completion: "20",
          decimations: "6",
          work_scope: true,
          work_scope_items: [
            {
              icon: "/img/roadmap/packetcrypt-bandwidth-hard-proof-of-work.webp",
              title: "PacketCrypt Bandwidth-Hard Proof-of-Work",
              descr: "PacketCrypt is the proof-of-work for the PKT blockchain. It was specifically designed to economically incentivize people to connect their internet bandwidth and power the PKT blockchain. PKT mining yields are directly tied to each user’s bandwidth contributions. PacketCrypt is the key to the PKT project because it ensures that the project is not reliant on centralized operators or infrastructure. It both secures the blockchain and scales a decentralized internet infrastructure powered by the people.",
            },
            {
              icon: "/img/roadmap/pkt-cash-cryptocurrency.webp",
              title: "PKT Cash Cryptocurrency",
              descr: "PKT Cash is the native cryptocurrency that is earned from mining the PKT blockchain. The prospect of earning PKT Cash is what incentivizes PKT miners to power the expansion and maintenance of the PKT Network’s decentralized internet infrastructure. The inception of PKT Cash is rooted in the belief that access to a fast and private internet should be universal. These incentives are what has galvanized the growing PKT community to own and operate the peer-to-peer PKT network and PKT blockchain.",
            },
            {
              icon: "/img/roadmap/pkt-command-line-wallet.webp",
              title: "PKT Command Line Wallet",
              descr: "The PKT Command Line Wallet (CLI) was developed as a foundational tool for interacting with the PKT blockchain. Its creation was driven by the necessity for a secure, efficient, and versatile wallet that could receive, send, and mine PKT. The CLI wallet can be installed and operated from a command line or terminal instance. It is also the foundational core for many graphical interface wallets.",
            },
            {
              icon: "/img/roadmap/mainnet-launch.webp",
              title: "Mainnet Launch",
              descr: "The mainnet launch on August 20, 2019 (Paris Time) marked the inception of the PKT blockchain. The mainnet launch was announced publicly as a fair mine, with no pre-mine, no founder shares, no team shares and no investors. By design, the PKT project is an open source, decentralized blockchain project built on Bitcoin’s btcd code base. It replaces Bitcoin’s SHA-256 proof-of-work with PacketCrypt. The other key changes to Bitcoin are 60 second block times and the addition of the Network Steward. The Network Steward is a wallet address that receives 20% of every mined block, as a self-funding mechanism for network development",
            },
            {
              icon: "/img/roadmap/pkt-cash-website.webp",
              title: "PKT.Cash Website",
              descr: "The first www.PKT.Cash website was built as a community-powered informational site about the PKT project. Contributors to the project are able to build and suggest pages to be added to the websites. It was created to be an information hub that could support the growing PKT community around the PKT blockchain and as a platform for education, engagement, and collaboration within the PKT ecosystem.",
            },
            {
              icon: "/img/roadmap/pkt-block-explorer.webp",
              title: "PKT Block Explorer",
              descr: "The PKT block explorer was developed as one of the first Network Steward funded projects. It provides transparency and accessibility into the PKT Network's blockchain activities and was created as a user-friendly tool to foster trust and engagement within the community. The block explorer allows users to easily track transactions, wallet balances, and network statistics.",
            },
            {
              icon: "/img/roadmap/gridfinity-pkt-mining-pool.webp",
              title: "Gridfinity PKT Mining Pool",
              descr: "The Gridfinity PKT Mining Pool emerged as one of the first community-operated PKT mining pools. Gridfinity was a pioneer in the early days of the blockchain. The Gridfinity team also contributed resources to simplify wallet setup for new PKT miners interested in mining PacketCrypt.",
            },
            {
              icon: "/img/roadmap/gridnode.webp",
              title: "Gridnode",
              descr: "A Gridnode was the first consumer hardware device sold by Gridfinity to mine PKT. The Gridnode was conceived to minimize the complexities and technical barriers associated with setting up a PKT node for mining. As a solution, each Gridnode had a hardware wallet and began mining PKT as soon as plugged in, making it accessible to a wider audience. Its creation marked a significant step towards democratizing the PKT Network, enabling more users to benefit from and contribute to its decentralized infrastructure.",
            },
            {
              icon: "/img/roadmap/pkt-cash-website.webp",
              title: "PKT Yellowpaper",
              descr: "The PKT yellowpaper outlines the technical specifications of PacketCrypt. The paper was co-authored by blockchain architect Caleb James DeLisle and mathematician Vishnu Seesahai, who are both leading technologists and thinkers within the PKT community. The PacketCrypt proof-of-work is a cornerstone for developers, contributors, and enthusiasts to understand, develop, and innovate within the PKT ecosystem.",
            },
            {
              icon: "/img/roadmap/pkt-pool-dashboard.webp",
              title: "PKT Network Whitepaper",
              descr: "The PKT whitepaper is the seminal document articulating the vision, architecture, and economic model of the PKT Network. Crafted by founding community members Caleb James DeLisle and Jesse Berger, this whitepaper lays out the vision and aspirations of creating a decentralized network infrastructure powered by blockchain technology. It provides a detailed blueprint for how the PKT Network aims to incentivize bandwidth sharing and serves as a manifesto for the new era of internet freedom and accessibility.",
            },
            {
              icon: "/img/roadmap/pkt-electrum-wallet.webp",
              title: "PKT Electrum Wallet",
              descr: "The PKT Electrum Wallet was developed as a Network Steward-funded proposal to create a lightweight, secure, and user-friendly wallet for managing PKT Cash. Designed as a fork of Bitcoin’s electrum, the wallet mirrors the ethos of PKT, prioritizing decentralization and security. However, the wallet does not function as a mining wallet. PKT Electrum has numerous features such as naming wallet addresses and a 15-word seed, making holding and managing PKT easier.",
            },
            {
              icon: "/img/roadmap/zulu-wallet.webp",
              title: "Zulu Wallet",
              descr: "Zulu wallet was developed as a Network Steward-funded proposal. It emerged from the necessity for a versatile and user-friendly graphical interface wallet that allowed PKT mining. It also addressed the needs from early PKT miners who needed to recover mining wallets that used the early hex seeds. The Zulu wallet was only maintained for 2 years and is no longer recommended for use.",
            },
            {
              icon: "/img/roadmap/community-launch.webp",
              title: "Community Launch",
              descr: "The PKT community launch was a Network Steward-funded, team-driven project. It was orchestrated by a collective of passionate people who all contributed their mind share and consistent effort to create the social and web-based foundation of the project. This launch included publishing articles, explanation videos, influencer reviews, social content creation, and community management efforts emphasizing collaboration and open-source principles. This set the stage for the initial awareness, growth and development of the ecosystem.",
            },
            {
              icon: "/img/roadmap/otc-trading-room.webp",
              title: "OTC Trading Chat",
              descr: "The OTC (Over-The-Counter) trading chat is a telegram chat that was launched by community members to enable peer-to-peer trading prior to PKT listing on any exchanges. This initiative included software development to track price and build an order book for matching buyers and sellers. The OTC trading chat embodies the decentralized spirit of the PKT project and is still accessible via Telegram.",
            },
            {
              icon: "/img/roadmap/mining-pool-software-update.webp",
              title: "Mining Pool Software Update",
              descr: "The mining pool software update was released as improvements that resulted in a significant reduction in the time it takes to compute proof trees associated with block mining. With this update, in most observed cases, the tree is complete before the next block arrives. This helped pools ensure there is almost no time spent not mining. A more in depth explanation of this update can be found here.",
            }
          ]
        },
        {
          number: "02",
          title: "Utility",
          description: "The Utility era of PKT focused on expanding utility and growing the network. This meant creating apps and services so people could actually use the PKT blockchain and PKT Network. When the network first started during the Launch era, mining PKT was easier because there weren't as many people doing it. There were a few active PKT mining pools, which meant the difficulty of mining was lower due to less competition for bandwidth and processing power.",
          description_2: "Following the Launch era, the Utility era was a period of hyper growth of the network infrastructure. A big part of this was attributed to PKT mining. As more people began mining, this decentralized the network's infrastructure.",
          description_3: "The Utility era also saw the launch of many new community-run apps and services. This included the launch of PKT VPN, the Route Server for processing network traffic, a simplified mining app called Minr, a WPKT bridge to Binance Smart Chain, new exchange listings, and the first Edge Point nodes helping people get online via mesh networking.",
          description_4: "The Utility era was just the beginning of the network’s real-world utility, setting the stages for bigger developments in the future Scale and Innovate eras.",
          title_1: "Projects Completed",
          title_2: "Months of Phase",
          title_3: "Decimations",
          pr_completed: "18",
          months_completion: "18",
          decimations: "5",
          work_scope: true,
          work_scope_items: [
            {
              icon: "/img/roadmap/route-server.webp",
              title: "Cjdns Route Server",
              descr: "The Route Server bridges cjdns and PKT to optimize internet traffic within the PKT Network. The Route Server works as a special broadcasting protocol designed to enhance the interoperability between cjdns's encrypted mesh network and the PKT Network. This is used for powering decentralized VPN services and connectivity with Web 3 dapps and services. The high performance of the Route Server is fundamental to routing traffic through the PKT Network and connecting to the traditional internet.",
              descr_2: "The project development resulted in a number of libraries being created, including, cjdnskeys - tools for working with cjdns keys, cjdnsann - library for parsing cjdns announcement messages, cjdnsniff - library for sniffing and injecting cjdns traffic, cjdnsadmin - admin API connector for talking to cjdns engine, cjdnsencode - parser and serializer for cjdns encoding schemes, cjdnsctrl - tool for parsing/serializing CTRL messages, cjdnshdr - tools for parsing and serializing cjdns packet headers, and netchecksum - library which implements the 1s complement checksum used by TCP, UDP and ICMP.",
            },
            {
              icon: "/img/roadmap/pkt-vpn.webp",
              title: "PKT VPN",
              descr: "Anodium VPN was developed as a Network Steward-funded project. It enables users to get a base-line VPN for free and have the option to pay for faster speed using PKT Cash. PKT VPN leverages cjdns exit nodes for VPN access points. The VPN server enables community members to create VPN exits, become listed as inventory on the app, and earn PKT when users pay for connectivity. The servers allow inbound connections, give a virtual IP address, and route traffic.",
            },
            {
              icon: "/img/roadmap/pkt-vpn-android-app.webp",
              title: "PKT VPN - Android App",
              descr: "Using PKT’s open-source PKT VPN technology, this user-ready Android app combines PKT VPN with a mobile PKT wallet. This enables users to pay for high speed VPN access, as well as e-commerce within the PKT Network. The PKT VPN app is built to evolve as a gateway to the PKT Network. Users have access to free VPN service, and the app can eventually combine with a browser that opens accessibility to tools, resources and services built in the PKT Network.",
            },
            {
              icon: "/img/roadmap/pkteer-pool.webp",
              title: "Pkteer Pool",
              descr: "The Pkteer pool was established in 2021 as a competitive mining pool in the PKT ecosystem. Its focus was to deliver high yields to announcement miners, incentivize infrastructure expansion of the network and to create inclusive and accessible mining for the PKT Network. Pkteer pool assisted other competitive pools to start up. Aimed at democratizing the mining process, it enabled miners with varying levels of technical expertise and hardware to contribute to and benefit from the network's growth. Pkteer pool operated until 2023 when it shut down.",
            },
            {
              icon: "/img/roadmap/pkt-world-pool.webp",
              title: "PKT World Pool",
              descr: "The PKT World pool was launched in 2021 to compete for mining rewards and offer miners alternative mining pool choices. The PKT World pool launched with an open paymaker so miners could review miner share payouts via a transparent mining experience. The PKT World pool ethos was to ensure stability of the PKT blockchain and promote equitable rewards distribution. The PKT World pool promotes itself as an inclusive and supportive PKT mining pool.",
            },
            {
              icon: "/img/roadmap/pkt-world-explorer.webp",
              title: "PKT World Block Explorer",
              descr: "The PKT World pool built a PKT block explorer as an essential tool for enhancing transparency on the PKT blockchain. The PKT World block explorer was the first platform to display PKT mining pool winning percentages. This provided the PKT community visibility into which pools were winning what percentage of the blocks. The PKT World block explorer also enables miners to enter their PKT wallet address to track their mining yields and PKT pool payouts. The PKT World block explorer reflects PKT World’s commitment to transparency. It provides a valuable resource for users to navigate the PKT blockchain and gain a deeper understanding of the blockchain’s functionality.",
            },
            {
              icon: "/img/roadmap/pkt-pool.webp",
              title: "PKT Pool",
              descr: "PKT Pool launched its competitive mining pool in 2021. Initially powered with substantial infrastructure, PKT Pool offered PKT miners increased yields based on its winning percentage. PKT Pool operated using an open paymaker, allowing miners to transparently view miner share payouts. The pool was available publicly until 2023 when it shut down.",
            },
            {
              icon: "/img/roadmap/pkt-pool-dashboard.webp",
              title: "PKT Pool Dashboard",
              descr: "PKT Pool launched a block explorer and custom dashboard for the PKT blockchain. This user-friendly interface included several compelling features, including a node explorer. The node explorer provided a visual representation of the PKT blockchain and its associated wallet addresses. The PKT Pool dashboard also provided comprehensive insights into mining performance, earnings, and network status. The PKT Pool dashboard is no longer accessible.",
            },
            {
              icon: "/img/roadmap/zetahash-pool.webp",
              title: "Zetahash Pool",
              descr: "The first iteration of the competitive Zetahash pool began in 2021. Powered by substantial processing power and high throughput bandwidth, Zetahash has been a force within the PKT blockchain ecosystem. Zetahash uses numerous proprietary techniques to achieve high win rates without providing a publicly available paymaker. Zetahash also uses a variable miner-share to reward miners that follow its recommended mining settings and prioritize Zetahash in their mining pool order. Zetahash also offers alternative mining end points that favor miners with lower bandwidth or higher bandwidth. This versatility is beneficial so that miners on lower throughput residential connections are able to participate. Zetahash’s infrastructure drives a competitive win rate against other pools.",
            },
            {
              icon: "/img/roadmap/pkt-cube.webp",
              title: "PKT Cube",
              descr: "The PKT Cube was developed by community-member company PKT Pal (company named changed to Routie). The PKT Cubes are designed as the first Edge Point nodes in the PKT Network (as referenced per the Whitepaper). These devices act as turnkey, dedicated PKT mining devices, without requiring any software installation. The devices also run a proprietary operating system called PkteerOS. PkteerOS was designed to push new software features as development of the project continues. This compact, user-friendly device was built to lower the barriers to entry for network participation, offering plug-and-play functionality to earn PKT by mining. The device also uses PKT Network for connectivity and has a wifi chip, so it can do wifi sharing as the PKT technology evolves.",
            },
            {
              icon: "/img/roadmap/wpkt-binance-smart-chain.webp",
              title: "WPKT - Binance Smart Chain",
              descr: "WPKT is an integration with Binance Smart Chain (BSC) that strategically bridges PKT in the ecosystem of EVM (Ethereum Virtual Machine) and the broader ecosystem of decentralized finance (DeFi). Recognizing the opportunity to connect to BSC's efficient, low-cost transaction environment and expansive user base, the creation of WPKT on BSC aimed to enhance liquidity, accessibility, and utility for PKT holders. WPKT can be held in a MetaMask wallet and opens the door for expansive use cases.",
            },
            {
              icon: "/img/roadmap/odapp-bridge.webp",
              title: "ODapp Bridge",
              descr: "ODapp is a bridge that enables people to swap PKT into WPKT and WPKT into PKT. The ODapp bridge provides seamless interoperability between BSC and PKT. The bridge was developed as a decentralized application (DApp). This innovation represents a strategic move enabling users to effortlessly move assets between networks, thereby expanding the utility and reach of the PKT Network.",
            },
            {
              icon: "/img/roadmap/pkt-watch-website.webp",
              title: "PKT Watch Website",
              descr: "PKT Watch is a community-member operated website that serves as a comprehensive resource and monitoring tool for the PKT Network. PKT Watch features several modules for monitoring tools and services within the PKT ecosystem. These include a Mining Calculator, which computes projected yields based on different hardware CPUs. Decimation Tracking, which provides a real-time countdown until the next decimation. PKT Documentation, which is a repository for documentation relating to the PKT project. As well as modules for unique apps developed by PKT Watch for the PKT ecosystem. This platform embodies the community's commitment to fostering an informed and engaged PKT ecosystem.",
            },
            {
              icon: "/img/roadmap/minr.webp",
              title: "Minr",
              descr: "Minr is an app built by PKT Watch to streamline and enhance the PKT mining process. Recognizing the complexities and technical challenges faced by PKT miners, Minr was developed as an easy solution to provide a more intuitive and efficient mining experience. This app was designed with the goal of making mining accessible to a wider audience. Thereby it provides a user-friendly mining interface that is accessible from both Windows, MacOS and Linux operating systems. The interface enables miners to control their PKT pool configuration, change CPU allocation, and choose which wallet address to mine into.",
            },
            {
              icon: "/img/roadmap/pkt-world-wallet.webp",
              title: "PKT World Wallet",
              descr: "The PKT World wallet is a desktop wallet for Windows, MacOS, and Linux. The PKT World wallet includes fast sync technology, which is useful when recovering seeds from legacy wallets or mining wallets that have a lot of transactions. The PKT World wallet can sync 12-word and 15-word seeds, as well as hex seeds used by legacy wallets. The PKT World wallet also has built-in PKT mining capabilities. Users can choose how many CPU cores to allocate and can mine directly into a wallet address. These PKT mining capabilities within the app simplifies PKT mining and serves as a pivotal tool in empowering users with a secure and straightforward interface.",
            },
            {
              icon: "/img/roadmap/pkt-lightning-network.webp",
              title: "PKT Lightning Network",
              descr: "The PKT Lightning Network was developed to enhance the scalability and speed of transactions within the PKT ecosystem. Built as a fork of Bitcoin’s Lightning Network, it was designed to facilitate instant, low-cost payments between nodes on the PKT Network. This development aimed to address the inherent scaling limitations of traditional layer 1 blockchain. PKT Lightning propels the PKT Network towards greater efficiency and facilitates its vision for enabling near-instant settlement and near-infinite transactions per second within the PKT Network.",
            },
            {
              icon: "/img/roadmap/anode-ios-wallet.webp",
              title: "Anode iOS Wallet",
              descr: "The Anode iOS Wallet was developed to meet the growing demand among PKT Network users for a mobile PKT wallet experience on iPhone. The Anode iOS wallet incorporates PKT Lightning Daemon (PLD), which expands the utility of the wallet for future integrations with PKT VPN.",
            },
            {
              icon: "/img/roadmap/exchange-listings.webp",
              title: "Exchange Listings",
              descr: "The community created a listing support team to help onboard PKT into exchanges. Since PKT is a fully decentralized project, the effort to list PKT requires a community effort and investment. Since PKT is a clone of Bitcoin’s btcd codebase, exchange integrations have been relatively easy, and the listing support team has ensured that exchanges listing PKT get the technical and documentation support they need to resolve issues quickly. Recognizing the importance of integrating PKT into established exchanges, listings enhance the visibility of the PKT project, thereby supporting the growth and adoption of the PKT Network.",
            }
          ]
        },
        {
          number: "03",
          title: "Scale",
          description: "The Scale era of the PKT Lightning Network marks a significant leap towards enhancing the network's growth and utility. This period focuses on ease of access to the network, broadening payment options for users and website owners, and introducing tokenization via TokenStrike.",
          description_2: "A primary aim during the Scale era is to simplify the process for both technical and non-technical users to set up functional websites on the PKT Network. This includes straightforward access to web hosting and reverse VPN services. Reverse VPN makes it so websites built on the PKT Network’s censorship-resistant framework are accessible through mainstream web browsers like Google Chrome and Safari. The PKT Network is accessible via VPN. Making the VPN app work across all operating systems is a priority for the Scale era. As the number of websites built in PKT Network increases, enhancing search engine capabilities and integrated wallet functionality will grow in importance.",
          description_3: "This Scale era also aims to make the internet globally accessible through mesh networking, bypassing traditional ISP connections. It's important that non-technical users and local governments can easily set up hardware antennas for internet sharing. This functionality is already possible, but there is a need for a free, user-friendly app interface to facilitate it.",
          description_4: "The Scale era will expand the PKT blockchain’s foundational features. Most notably with the introduction of PKT Lightning for near-instant payment processing and TokenStrike for handling multi-currency ledgers. TokenStrike is expected to foster the development of new cryptocurrencies and decentralized exchanges within the PKT ecosystem. TokenStrike is uniquely designed so that each new cryptocurrency operates on its own blockchain, ensuring interoperability without burdening the main PKT chain. This approach will support both fungible and non-fungible tokens, such as for bandwidth leasing.",
          description_5: "Additionally, the inclusion of smart contract functionality is anticipated. This can be achieved by adapting Stacks, a Layer 2 solution for Bitcoin that offers smart contract programming, further expanding PKT’s utility.",
          title_1: "Projects Completed",
          title_2: "Months of Phase",
          title_3: "Decimations",
          pr_completed: "5",
          months_completion: "6",
          decimations: "3",
          work_scope: true,
          work_scope_items: [
            {
              icon: "/img/roadmap/wifi-sharing-hardware.webp",
              title: "Wifi Sharing Hardware",
              descr: "In order to scale global internet sharing, the PKT Network needs compatible wifi hotspot hardware. Community member-company Routie.io has developed the first hardware antennas, called Edge Extenders. These antennas work as guest wifi access points. While Routie sells its antennas, this technology is open source so it can now be incorporated into third party hardware. This project is complete.",
            },
            {
              icon: "/img/roadmap/governance-system-update.webp",
              title: "Electorium - Network Steward Governance Update",
              descr: "Electorium is an update to the Network Steward governance system. Recognizing the importance of community input and governance, this update was crafted to empower network participants with a more inclusive, responsive, and decentralized ecosystem. Previously, the Network Steward rules required votes from more than 50% of the mined PKT to change who is Network Steward. However, the vote count failed to account for burned coins. This new system enables anyone to become a candidate when elected with over 50% of the electorate. Phase 1 enables anyone to vote by proof-of-stake, using the wallet balance of a wallet address. If a vote goes for someone who does not wish to be a candidate, their vote is delegated to whoever they vote for. If a candidate explicitly votes for themself, their vote is the same as indicating their candidacy. A new election for who becomes Network Steward is automatically held every 7 days. The Electorium algorithm is implemented in Rust and Golang and has received extensive fuzz testing to verify correctness. Phase 2 of Electorium will enable the winning candidate to automatically receive the NS blockchain payments to the winning wallet address. Phase 2 will require a soft fork, which is planned for later in 2024 or early 2025. Phase 1 of this project is complete.",
            },
            {
              icon: "/img/roadmap/network-steward-voting-app.webp",
              title: "PKT Voter App",
              descr: "PKT Voter was developed as a graphical interface for Electorium, which enables PKT wallet holders to vote proof-of-stake. This application facilitates the voting process, allowing PKT holders to vote the balance of their wallet, without transmitting any PKT during voting. The PKT Voter app underscores the community's commitment to democratic principles, decentralized governance and ensures that the development and allocation of resources within the PKT Network are aligned with the will of the majority of the voters. This project is complete.",
            },
            {
              icon: "/img/roadmap/yunohost-website-builder.webp",
              title: "PKT Website Builder",
              descr: "The PKT website builder is designed to simplify the web development process in the PKT Network. Using a user-friendly website building tools aim to lower the barriers to entry to receive an IPv6 web URL and create a peer-to-peer hosted website using cjdns. Cjdns websites populate and expand the PKT Network. Recognizing the challenge that non-technical users face in the digital space, the PKT website building enables users to launch a censorship-resistant wordpress website in the PKT Network. This project is complete."
            },
            {
              icon: "/img/roadmap/pkt-network-web-hosting.webp",
              title: "PKT Network Web Hosting",
              descr: "A web hosting platform is being built to further simplify setting up cjdns websites in the PKT Network. This web hosting platform will enable users to rent a virtual private server (VPS) with Wordpress pre-installed. Users will be able to pay using PK Cash for the VPS. Users will also be able to choose if the website is only accessible peer-to-peer within the PKT Network, or uses a reverse VPN so the website is accessible from traditional web browsers. Leveraging the PKT blockchain's infrastructure, this PKT Network web hosting offers an alternative to traditional web hosting services, ensuring greater resilience, privacy and security. By decentralizing the hosting process, PKT Network Web Hosting empowers users to maintain control over their online presence while contributing to the growth and decentralization of the PKT ecosystem. This project is under active development."
            },
            {
              icon: "/img/roadmap/paid-vpn.webp",
              title: "Paid VPN",
              descr: "PKT VPN is designed as a free, decentralized VPN service that operates within the PKT Network. Paid VPN has been successfully demo’d and enables users to pay for faster VPN speeds. Instead of a subscription-based model, Paid VPN offers users premium VPN services on a pay-per-use basis. The value exchange occurs between the user and the VPN exit provider. Phase 1 is completed. Phase 2 of implementing Paid VPN into PKT VPN for public use is under-development."
            },
            {
              icon: "/img/roadmap/zulu-wallet.webp",
              title: "PKT Pay",
              descr: "PKT Pay is a tool being developed to be a streamlined, multi-currency payment solution within the PKT ecosystem. Since websites built in the PKT Network can use their IPv6 web URL as a PKT payment address, there is a need for seamless transactions between users, merchants, and service providers. PKT Pay is aimed to be a user-friendly payment gateway that enhances the usability and adoption of PKT Cash. Merchants using PKT Pay will be able to accept payment for goods and services in various different cryptocurrencies, such as Bitcoin, or Ethereum, or fiat currency such as credit card. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/pkt-vpn-desktop-app.webp",
              title: "PKT VPN Desktop App",
              descr: "PKT VPN was initially developed as a free-to-use Android app, with an integrated PKT wallet. To expand PKT VPN’s utility and usability, it is now being developed as a desktop app for Windows and MacOS operating systems. Initially this desktop app will only feature PKT VPN, with no wallet. This desktop app can help expand user access to the PKT Network and increase utility of the network. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/exchange-listings.webp",
              title: "PKT DNS",
              descr: "Developing a DNS (Domain Name System) for PKT would leverage the mesh network infrastructure to map domain names to cjdns IP addresses. This setup would ensure that DNS requests are secure, private, and resistant to censorship. By distributing DNS services across multiple nodes, the PKT Network can ensure that web address lookups are efficient, resilient to attacks, and free from centralized control, embodying the network's ethos of decentralization and privacy. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/stacks-integration.webp",
              title: "Stacks Integration",
              descr: "Smart contract functionality is a key milestone in diversifying the utility of the PKT Network. This includes supporting DeFi, decentralized bandwidth trading marketplaces, RWAs (real world assets), colored coins, NFTs, and decentralized media distribution. Since PKT is a clone of the btcd Bitcoin codebase, it’s possible to fork Stacks, which is Bitcoin’s Layer 2 solution. This will deliver PKT a robust smart contract platform with advanced functionality. This integration aims to expand the capabilities of PKT, fostering innovation and enabling developers to build decentralized applications (dApps) and smart contracts that further drive adoption and diverse use cases for the PKT ecosystem. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/ordinals-integration.webp",
              title: "Ordinals Integration",
              descr: "Ordinal technology involves inscribing arbitrary data onto individual satoshis, effectively turning them into unique, identifiable, and transferable digital artifacts. Since PKT uses the same codebase as Bitcoin, it is possible to inscribe onto nPKTs, opening up avenues for incorporating unique, traceable, and potentially valuable digital assets directly into its ecosystem. This technology can be used for tokenized assets such as RWAs (real world assets), digital collectibles, NFTs, digital identity credentials, and DeFi innovations. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/pkt-world-explorer.webp",
              title: "PKT Search",
              descr: "PKT Network is its own sovereign network within the larger internet. Websites built in the PKT Network are accessible peer-to-peer within the network, or can be reached from traditional web browsers using a reverse VPN service. PKT Network will need its own efficient search engine so users can search websites within the PKT ecosystem. This will offer users a reliable and decentralized method for discovering content and information within PKT’s decentralized web. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/gridnode.webp",
              title: "Wifi Access Point Hotspot Map",
              descr: "PKT Network wifi access points are distributed across the world. Creating a hotspot map will help visualize the distribution of network nodes and be a tool for users to locate nearby hotspots and network infrastructure. By showcasing the global distribution of PKT nodes, a hotspot map will provide valuable insights into the network's reach. This can also facilitate the expansion efforts for global wifi access points. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/pkt-electrum-wallet.webp",
              title: "PKT Hub",
              descr: "PKT Network is built to support decentralized media distribution. PKT Hub is a decentralized media platform that is accessible through the PKT Network. PKT Hub enables media companies and content creators to host next gen, library app/channels through which media content can be distributed. Netflix, Hulu and HBO are examples of legacy library apps. PKT Hub functions like Roku, but enables anyone to launch a library app/channels. Content can be accessible via subscription, or pay-per-view. Library app owners will not pay any platform fees. Library apps will have the ability to use traditional payment processing services, or PKT Pay. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/pkt-watch-website.webp",
              title: "PKT TV",
              descr: "PKT TV originated from the vision of creating a decentralized media platform within the PKT ecosystem. PKT TV will be available as a library app within PKT Hub. Designed to offer viewers access to a diverse range of content, including feature films, and TV shows, PKT TV provides a decentralized media alternative to traditional media distributors and platforms. By leveraging PKT's decentralized infrastructure and integrated payment rails, PKT TV will have no platform fees or distribution fees. This ensures all revenue reaches the talent and investors that create the content. This project is currently in a research phase."
            },
            {
              icon: "/img/roadmap/token-strike.webp",
              title: "TokenStrike",
              descr: "TokenStrike will become PKT’s token issuance protocol, similar to ERC-20 for Ethereum. Conceived as a solution to enable multi-currency ledger functionality within the PKT ecosystem, what makes TokenStrike unique is each token supply is its own blockchain. This ensures that token pairs are horizontally transmutable, but issuance and transaction validation does not congest the network for maximizing scalability. TokenStrike is designed to make it possible to issue tokens and NTFs with near-zero cost. This functionality is required so Edge Points can easily tokenize bandwidth and trade tokens in a decentralized bandwidth trading marketplace (PKT Dex). TokenStrike enables atomic swaps using nominal PKT Lightning Network integration. TokenStrike will empower users to tokenize assets, conduct cross-chain transactions, and unlock new possibilities for DeFi applications. TokenStrike development is currently paused while sourcing a new, reliable development team."
            }
          ]
        },
        {
          number: "04",
          title: "Innovate",
          description: "The Innovate era of PKT is the phase of expanding consumer applications that aim to replace traditional, centralized tools and services. This era is focused on enhancing the network's scalability, interoperability, and capacity for handling high volumes of transactions. It targets various areas including bandwidth markets, decentralized exchanges, content delivery networks, media distribution, social networks, and supply chain efficiencies.",
          description_2: "This period will also see the further emergence of Cloud ISPs, boosting the bandwidth market's dynamism and competitiveness. Users will have the opportunity to lease bandwidth guarantees, enabling internet service without relying on traditional ISPs. Improvements to cjdns compact source routing will enhance network resiliency and optimize the balance between router performance and cost. Additionally, advancements in the PKT Lightning Network will introduce new features into both mobile and desktop wallet technologies, enhancing the speed and throughput of payments.",
          description_3: "Overall, the Innovate era will help PKT become one of the most open, high-performant, and versatile decentralized networks globally. This era aims to strengthen the network's infrastructure and blockchain so free and open internet access and e-commerce is accessible and sustainable worldwide.",
          work_scope: false,
        },
      ],
    };
  },
  head() {
    return {
      title: "Roadmap | PKT Cash",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'This roadmap provides an overview of the PKT ecosystem development, separated into four phases: Launch, Utility, Scale, and Innovate. Each phase defines an era of focus. Therefore, community developers and contributors have a guide for what tools, functionality and capabilities are needed and which relate to each era.'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          content: 'Roadmap | PKT Cash'
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: 'This roadmap provides an overview of the PKT ecosystem development, separated into four phases: Launch, Utility, Scale, and Innovate. Each phase defines an era of focus. Therefore, community developers and contributors have a guide for what tools, functionality and capabilities are needed and which relate to each era.'
        }
      ],
      link: [
        {
          rel: 'canonical',
          href: 'https://pkt.cash' + this.$route.path
        }
      ]
    };
  },
};
</script>
<style lang="scss">
.v-roadmap {
  background-color:$black_blue;
  position:relative;
  overflow-y:hidden;
  &:before {
    content:'';
    background-image:url(/img/roadmap-layer-top.webp);
    position:absolute;
    top:0;
    right:0;
    width:rem(950);
    height:rem(1500);
    background-position:right top;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
    @include for-width(-desktop-lg) {
      width:rem(750);
      height:rem(1200);
    }
    @include for-width(-laptop_small) {
      width:rem(500);
      height:rem(600);
    }
    @include for-width(-small-lg) {
      width:100%;
      height:rem(700);
      background-position:right -75px top;
    }
  }
  &:after {
    content:'';
    background-image:url(/img/roadmap-layer-bottom.webp);
    position:absolute;
    bottom:-10%;
    left:0;
    width:75%;
    height:80%;
    background-position:left top;
    background-size:contain;
    background-repeat:no-repeat;
    z-index:1;
  }
  & > section {
    z-index:3;
    position:relative;
  }
  & .c-spot-a-internal {
    padding:rem(165) 0 rem(15);
    @include for-width(-small-lg) {
      padding:rem(170) 0 rem(25);
    }
  }
  & .v-tabs-nav {
    & .nav-tabs-navigation {
      & .nav-tabs {
        @extend %df;
        @extend %jcc;
        @extend %aic;
        width:100%;
        border-bottom:1px solid rgba(217,217,217,.3);
        @include for-width(-small-lg) {
          padding:0 rem(20);
          justify-content: space-between;
        }
        &:before,&:after {
          display:none;
        }
        & .tab {
          @extend %db;
          width:auto;
          @include for-width(-small-lg) {
            width:50%;
          }
          & .tabs__link {
            border:0;
            font-size: rem(16);
            line-height: rem(30);
            @extend %inter_semibold;
            color:$white_50;
            border-bottom:2px solid transparent;
            padding:rem(18) rem(28);
            border-radius:0;
            margin:0;
            &:hover {
              background:none;
              color:$white;
            }
            &.active_tab {
              color:$white;
              border-color:$green;
            }
          }
        }
      }
    }
    & .tab-content {
      & #p-Introduction {
        padding:rem(80) 0 rem(180);
        @include for-width(-small-lg) {
          padding:rem(45) 0 rem(140);
        }
      }
    }
    & .v-introduction__inner {
      @extend %dg;
      -ms-grid-columns: 38% 62%;
      grid-template-columns: 38% 62%;
      @include for-width(-tablet) {
        display:block;
      }
      &_left {
        & h2 {
          @extend %h2-common;
        }
      }
      &_right {
        padding-top:rem(50);
        @include for-width(-tablet) {
          padding-top:rem(35);
        }
        & p {
          @extend %p-big-common;
          margin-bottom:rem(25);
        }
      }
    }
    & .v-introduction__papers {
      padding:rem(115) 0;
      @extend %df;
      @extend %jcc;
      @extend %fw;
      @include for-width(-tablet) {
        padding:rem(95) 0;
      }
      @include for-width(-small-lg) {
        padding:rem(60) 0 rem(85);
        display:block;
      }
      &_single {
        margin:0 rem(20);
        border-radius:rem(20);
        padding:rem(13) rem(20) rem(20);
        @extend %t-center;
        width:rem(360);
        @include for-width(-tablet) {
          width:rem(320);
          margin:0 rem(10);
        }
        @include for-width(-small-lg) {
          width:100%;
          margin:rem(20) 0 0;
          padding:rem(15) rem(20) rem(30);
        }
        & p {
          @extend %p-common-bold;
          color:$black_blue;
        }
        & h4 {
          @extend %h3-common;
          color:$black_blue;
          margin:rem(10) 0 rem(20);
          @include for-width(-small-lg) {
            margin:rem(5) 0 rem(10);
          }
        }
      }
    }
    & .v-introduction__chess {
      & .c-chess-block {
        @include for-width(-small-lg) {
          margin-left:-15px;
          margin-right:-15px;
        }
        &_inner_single {
          padding-right:0;
          padding-left:0;
        }
        &_inner_single_img {
          & img {
            border-radius:rem(20);
          }
        }
      }
    }
    & .v-phases__inner {
      padding-bottom:rem(300);
      @include for-width(-laptop) {
        padding-bottom:rem(150);
      }
      &__navigation {
        @extend %dg;
          -ms-grid-columns: 1fr 1fr 1fr 1fr;
          grid-template-columns: 1fr 1fr 1fr 1fr;
          grid-gap: 0 rem(40);
          padding:rem(40) 0 rem(150);
          cursor:pointer;
          @include for-width(-laptop) {
            grid-gap: 0 rem(20);
            padding:rem(40) 0 rem(100);
          }
          @include for-width(-tablet) {
            -ms-grid-columns: 1fr 1fr;
            grid-template-columns: 1fr 1fr;
            grid-gap: rem(40) rem(40);
          }
          @include for-width(-small-lg) {
            padding:rem(20) 0 rem(85);
            grid-gap: rem(20) rem(20);
          }
          & .c-phase {
            border-radius:rem(20);
            padding:rem(30) rem(40);
            background-color:$black_blue_light;
            @include for-width(-small-lg) {
              padding:rem(10) rem(20) rem(15);
            }
            &:hover {
              background-color:$main_blue_light;
            }
            &:focus {
              background-color:$main_blue_light;
            }
            &__title {
              @extend %p-big-common-bold;
               @include for-width(-small-lg) {
                 text-align:center;
               }
            }
            &__img {
              display:block;
              width:auto;
              height:rem(108);
              margin:rem(20) auto rem(10);
              object-fit:contain;
              object-position:center;
              @include for-width(-small-lg) {
                height:rem(65);
                margin:rem(5) auto rem(15);
              }
            }
            &__number {
              position:relative;
              @extend %p-big-common;
              &:before {
                content:'';
                position:relative;
                width:rem(10);
                height:rem(10);
                border-radius:rem(50);
                margin-right:rem(20);
                display:inline-block;
                vertical-align:middle;
                background-color:$white;
              }
            }
          }
          & #Utility {
            & .c-phase__number {
              &:before {
                background-color:#0DA6E7;
              }
            }
          }
          & #Scale {
            & .c-phase__number {
              &:before {
                background-color:#00B187;
              }
            }
          }
          & #Innovate {
            & .c-phase__number {
              &:before {
                background-color:#F9882F;
              }
            }
          }
      }
      &__content {
        &__main {
          @extend %dg;
          -ms-grid-columns: 35% 65%;
          grid-template-columns: 35% 65%;
          @include for-width(-tablet) {
            display:block;
          }
          &_left {
            & h3 {
              @extend %h3-common;
              @include for-width(-tablet) {
                padding-bottom:rem(35);
              }
            }
          }
          &_right {
            & p {
              @extend %p-big-common;
              margin-bottom:rem(16);
              &:last-child {
                margin-bottom:0;
              }
            }
          }
        }
        &__analytics {
          padding:rem(135) 0 rem(130);
          @include for-width(-tablet) {
            padding:rem(100) 0;
            margin-left:-25px;
            margin-right:-25px;
          }
          @include for-width(-small-lg) {
            padding:rem(85) 0;
          }
          & .container {
            @extend %dg;
            -ms-grid-columns: 1fr 1fr 1fr;
            grid-template-columns: 1fr 1fr 1fr;
            grid-gap: 0 rem(40);
            @include for-width(-small-lg) {
              -ms-grid-columns: 1fr;
              grid-template-columns: 1fr;
              grid-gap: rem(20) 0;
            }
          }
          &_data {
            border-radius: rem(20);
            padding:rem(30);
            @extend %t-center;
            &__value {
              color:$black_blue;
              @extend %h2-common;
              @include for-width(-tablet-lg) {
                font-size: rem(36);
                line-height: rem(46);
              }
              @include for-width(-small-lg) {
                font-size: rem(30);
                line-height: rem(36);
              }
            }
            & hr {
              background-color:$black_blue;
              border:0;
              width:rem(120);
              height:rem(1);
              padding:0;
              margin:rem(20) auto rem(23);
              @include for-width(-small-lg) {
                display:none;
              }
            }
            &__title {
              color:$black_blue;
              font-size: rem(16);
              line-height: rem(24);
              @extend %inter_semibold;
            }
          }
        }
        &__scope {
          & h3 {
            @extend %h3-common;
            margin-bottom:rem(26);
            @include for-width(-small-lg) {
              margin-bottom:rem(20);
            }
          }
          &_single {
            @extend %dg;
            -ms-grid-columns: 100px 1fr;
            grid-template-columns: 100px 1fr;
            grid-gap: 0 rem(60);
            padding:rem(20) rem(40) rem(30) 0;
            border-top:1px solid rgba(255,255,255,.2);
            @include for-width(-tablet) {
              padding:rem(20) rem(20) rem(30) 0;
              grid-gap: 0 rem(40);
            }
            @include for-width(-small-lg) {
              display:block;
              padding:rem(25) 0 rem(30);
            }
            &_list {
              width:rem(100);
              height:rem(100);
              border-radius:rem(15);
              background-color:$black_blue_light;
              display:block;
            }
            &_text {
              & h5 {
                @extend %p-big-common-bold;
                margin-bottom:rem(7);
                @include for-width(-small-lg) {
                  margin-top:rem(25);
                }
              }
              & p {
                @extend %p-common-thick;
                // color:$white_50;
              }
            }
          }
        }
      }
    }
  }
}
</style>