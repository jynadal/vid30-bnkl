# How to Mint RWA (Real World Assets) - Complete Guide

## Overview

This NFT marketplace project built on the CHZ (Chiliz) network using Thirdweb allows you to mint RWA (Real World Assets) as NFTs. The platform treats RWAs as specialized NFTs with metadata that describes real-world assets like property, artwork, commodities, or any physical asset.

## Prerequisites

### 1. Environment Setup

First, ensure you have the following set up:

- Node.js installed on your system
- A wallet compatible with CHZ network (MetaMask recommended)
- CHZ tokens for gas fees
- Access to Thirdweb dashboard

### 2. Project Configuration

1. **Create Environment File**: Create a `.env.local` file in the root directory with:
   ```
   NEXT_PUBLIC_CLIENT_ID=your_thirdweb_client_id
   NEXT_PUBLIC_NETWORK=SpicyChain
   NEXT_PUBLIC_MARKET_CONTRACT_ADDRESS=your_marketplace_contract_address
   NEXT_PUBLIC_NFT_CONTRACT_ADDRESS=your_nft_contract_address
   ```

2. **Get Thirdweb Client ID**:
   - Log into your Thirdweb account
   - Navigate to "Settings" → "API Keys"
   - Copy your Client ID

3. **Deploy Smart Contracts**:
   - Deploy an NFT contract (ERC-721 or ERC-1155)
   - Deploy a Marketplace contract (v3)
   - Copy the contract addresses to your `.env.local` file

### 3. Install Dependencies

```bash
npm install
```

### 4. Start Development Server

```bash
npm run dev
```

## How to Mint RWA

### Step 1: Connect Your Wallet

1. Open the application in your browser (usually `http://localhost:3000`)
2. Click the "Connect Wallet" button
3. Select your wallet provider (MetaMask, WalletConnect, etc.)
4. Ensure you're connected to the CHZ network

### Step 2: Navigate to Mint Page

1. Click on the "Mint" card in the navigation grid
2. You'll be redirected to `/mint` page with the title "Mint new RWA"

### Step 3: Fill RWA Details

The minting form requires the following information:

1. **Title**: Name of the RWA (e.g., "Miami Beach Property #123")
2. **Description**: Detailed description of the real-world asset
3. **Cover URL**: Image URL representing the RWA (property photo, artwork image, etc.)
4. **Movie URL**: Additional media URL (video, 3D model, or documentation)

### Step 4: Submit for Minting

1. Fill all required fields
2. Click the "Mint" button
3. Confirm the transaction in your wallet
4. Wait for the transaction to be confirmed on the blockchain

## RWA Metadata Structure

The system uses the following metadata structure for RWAs:

```typescript
type MintMetadata = {
    metadata: {
        cover: string;        // Image URL of the asset
        title: string;        // Name of the RWA
        description: string;  // Detailed description
        external_url: string; // Additional media or documentation URL
    };
    to: string;              // Recipient address (auto-filled)
    supply: 1;               // Always 1 for unique RWAs
};
```

## After Minting

### View Your RWAs

1. Click on "Wallet" in the navigation
2. See all RWAs you own
3. View detailed information about each asset

### List RWAs for Sale

1. Navigate to your wallet
2. Select the RWA you want to sell
3. Set price and listing duration
4. Submit listing transaction

### Browse Marketplace

1. Click "Market" in the navigation
2. View all listed RWAs
3. Purchase available assets

## Technical Implementation Details

### Smart Contract Integration

The project uses Thirdweb's SDK for smart contract interactions:

- **NFT Contract**: Handles RWA minting and ownership
- **Marketplace Contract**: Manages listings, sales, and transfers

### Key Components

1. **Mint Page** (`src/pages/mint.tsx`):
   - Form interface for RWA details
   - Handles minting transactions
   - Validates required fields

2. **Contract Utilities** (`src/util/getContracts.ts`):
   - Manages contract connections
   - Handles marketplace and NFT contract instances

3. **Metadata Types** (`src/types/mintMetadata.ts`):
   - Defines RWA metadata structure
   - Ensures type safety

## Best Practices for RWA Minting

### 1. Asset Documentation

- Provide clear, high-quality images
- Include comprehensive descriptions
- Add relevant documentation URLs
- Consider legal compliance for asset representation

### 2. Metadata Quality

- Use IPFS for permanent image storage
- Include relevant keywords in descriptions
- Ensure external URLs are permanent and accessible
- Consider adding location data for physical assets

### 3. Legal Considerations

- Ensure you have rights to tokenize the asset
- Consider regulatory compliance in your jurisdiction
- Include appropriate disclaimers
- Maintain off-chain documentation linking to physical assets

## Troubleshooting

### Common Issues

1. **"Minting in progress" not updating**:
   - Check wallet connection
   - Ensure sufficient CHZ balance for gas
   - Verify contract addresses in `.env.local`

2. **Transaction Fails**:
   - Check network connection
   - Verify contract permissions
   - Ensure all required fields are filled

3. **Images Not Loading**:
   - Verify image URLs are accessible
   - Use IPFS for permanent storage
   - Check CORS settings for image hosts

### Gas Optimization

- Batch multiple operations when possible
- Use appropriate gas limits
- Monitor CHZ network congestion

## Advanced Features

### Custom Metadata

Extend the metadata structure by modifying `src/types/mintMetadata.ts`:

```typescript
export type MintMetadata = {
    metadata: {
        cover: string;
        title: string;
        description: string;
        external_url: string;
        // Add custom fields
        asset_type: string;
        location: string;
        appraisal_value: number;
        certification: string;
    };
    to: string;
    supply: 1;
};
```

### Batch Minting

For multiple RWAs, consider implementing batch minting functionality in the smart contract and updating the UI accordingly.

## Security Considerations

1. **Private Keys**: Never expose private keys in environment files
2. **Contract Verification**: Verify smart contracts on block explorers
3. **Access Control**: Implement proper access control for minting permissions
4. **Asset Verification**: Establish processes for verifying real-world asset ownership

## Conclusion

This NFT marketplace provides a complete solution for minting, trading, and managing RWAs on the CHZ network. The process is streamlined through Thirdweb's infrastructure, making it accessible for both developers and end-users to tokenize real-world assets efficiently.

For additional support, refer to the Thirdweb documentation and CHZ network resources.