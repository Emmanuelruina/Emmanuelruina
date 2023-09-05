import { bsc } from 'wagmi/chains'
import { publicProvider } from 'wagmi/providers/public'
import {
  configureChains,
  createClient,
  WagmiConfig,
} from 'wagmi'
const { provider: wagmiProvider, webSocketProvider } = configureChains([bsc], [publicProvider()])
const connector = new BinanceIDConnector({
  options: { chainId: 56, rpc: { 56: 'https://bsc-dataseed.binance.org/' } },
})

const client = createClient({
  provider: wagmiProvider,
  webSocketProvider,
})
export default function App() {
  return (
    <WagmiConfig client={client}>
      <Home />
    </WagmiConfig>
  )
}
