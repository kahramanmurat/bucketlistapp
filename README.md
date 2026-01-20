# Bucket List App

A modern full-stack application built with AWS Amplify, React, and Vite that allows users to create and manage their bucket list items with image uploads and secure authentication.

## Project Overview

The Bucket List App is a cloud-native application that leverages AWS Amplify Gen 2 for backend infrastructure. It provides users with a seamless experience to:
- Create and manage bucket list items with titles and descriptions
- Upload images for each bucket list item
- Secure authentication with email-based login
- Real-time data synchronization
- Responsive user interface

## Project Structure

```
bucketlistapp/
├── amplify/                          # AWS Amplify backend configuration
│   ├── auth/
│   │   └── resource.ts              # Authentication configuration (Cognito)
│   ├── data/
│   │   └── resource.ts              # Data model and GraphQL schema
│   ├── storage/
│   │   └── resource.ts              # S3 storage configuration for images
│   ├── backend.ts                   # Backend definition and exports
│   ├── package.json                 # Backend dependencies
│   └── tsconfig.json                # TypeScript configuration for backend
│
├── src/                             # Frontend source code
│   ├── App.jsx                      # Main React component
│   ├── App.css                      # App styling
│   ├── main.jsx                     # React entry point
│   ├── index.css                    # Global styles
│   └── assets/                      # Static assets
│
├── public/                          # Static files
├── index.html                       # HTML entry point
├── vite.config.js                   # Vite configuration
├── eslint.config.js                 # ESLint configuration
├── package.json                     # Frontend dependencies
├── amplify_outputs.json             # Auto-generated Amplify configuration
└── README.md                        # This file
```

## Technologies Used

### Frontend
- **React 19.2** - UI library
- **Vite** - Fast build tool and dev server
- **JavaScript** - Programming language
- **CSS3** - Styling

### Backend & Infrastructure
- **AWS Amplify Gen 2** - Full-stack framework
- **AWS Cognito** - Authentication & authorization
- **AWS AppSync** - GraphQL API
- **AWS DynamoDB** - NoSQL database
- **AWS S3** - Image storage
- **TypeScript** - Type-safe backend code

### UI Components
- **@aws-amplify/ui-react** - Pre-built Amplify UI components
- **aws-amplify** - Amplify client library

## Prerequisites

- **Node.js** 18+ and npm
- **Git** for version control
- AWS Account (for deployment)
- Amplify CLI (for local development and deployment)

## Getting Started

### 1. Installation

```bash
# Install frontend dependencies
npm install

# Install AWS Amplify and UI components
npm install aws-amplify @aws-amplify/ui-react
```

### 2. Local Development

```bash
# Start the development server
npm run dev
```

The app will be available at `http://localhost:5173`

### 3. Backend Configuration

The backend is automatically configured in the `amplify/` folder with:
- **Authentication**: Email-based login via AWS Cognito
- **Data Model**: GraphQL schema for BucketItem with owner-based authorization
- **Storage**: S3 bucket for image uploads with identity-based access control

## Features

### Current Features
- ✅ User authentication (email/password)
- ✅ Create bucket list items with title and description
- ✅ Image upload functionality
- ✅ Owner-based data access control
- ✅ Real-time data synchronization
- ✅ Responsive design

### Data Model

**BucketItem**
- `id` - Unique identifier
- `title` - Item title (required)
- `description` - Item description
- `image` - Image URL
- `owner` - User who created the item (auto-managed)

## API & Data Access

### GraphQL Operations

The app uses AWS AppSync for GraphQL API operations:
- Create, read, update, delete bucket items
- List all items for the authenticated user
- Real-time subscriptions for data changes

### Authorization Rules

- **Owner-only access**: Users can only access their own bucket list items
- **Unauthenticated access**: Not allowed (requires email login)

## Environment Variables

Create a `.env` file in the root directory if needed:

```bash
VITE_REGION=us-east-1
# Other Amplify config is auto-generated
```

## Building for Production

```bash
# Build the optimized production bundle
npm run build

# Preview the production build locally
npm run preview
```

## Deployment

### Deploy to AWS Amplify Hosting

```bash
# Install Amplify CLI if not already installed
npm install -g @aws-amplify/cli

# Initialize and configure Amplify
amplify init

# Deploy the backend
amplify push

# Deploy the frontend to Amplify Hosting
amplify publish
```

### Deploy to Other Platforms

The built files in the `dist/` directory can be deployed to:
- Vercel
- Netlify
- AWS S3 + CloudFront
- Any static hosting service

## Development Workflow

1. **Make changes** to frontend code in `src/`
2. **Update backend** in `amplify/` folder if needed
3. **Test locally** with `npm run dev`
4. **Push changes** to git: `git push origin main`
5. **Deploy** with `amplify publish`

## Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
npm run format       # Format code (if configured)
```

## Troubleshooting

### Common Issues

**Issue: Auth import error**
- Solution: Ensure `amplify/auth/resource.ts` properly exports `auth` object using `defineAuth()`

**Issue: Dependency warnings**
- Solution: These are mostly low-severity issues in bundled Amplify dependencies. Safe to ignore for development.

**Issue: Images not uploading**
- Solution: Check S3 bucket permissions and ensure authentication is working

## Security Considerations

- ✅ User authentication required for all operations
- ✅ Owner-based authorization on all data
- ✅ Images stored in S3 with identity-based access
- ✅ Sensitive data encrypted at rest
- ⚠️ Review AWS IAM policies before production deployment

## Performance

- Vite provides fast HMR (Hot Module Replacement) during development
- GraphQL queries are optimized with AppSync caching
- Images are stored in S3 with CDN acceleration
- DynamoDB provides low-latency data access

## Contributing

1. Create a feature branch: `git checkout -b feature/your-feature`
2. Make your changes
3. Test thoroughly
4. Commit: `git commit -am 'Add feature description'`
5. Push: `git push origin feature/your-feature`
6. Create a Pull Request

## License

This project is open source and available under the MIT License.

## Support

For issues and questions:
1. Check the [AWS Amplify Documentation](https://docs.amplify.aws/)
2. Review the [React Documentation](https://react.dev)
3. Check GitHub issues in this repository

## Useful Resources

- [AWS Amplify Gen 2 Docs](https://docs.amplify.aws/gen2/)
- [React Documentation](https://react.dev)
- [Vite Documentation](https://vitejs.dev)
- [GraphQL Documentation](https://graphql.org)
- [AWS AppSync](https://aws.amazon.com/appsync/)

## Roadmap

- [ ] Social sharing features
- [ ] Collaboration with friends
- [ ] Bucket list categories/tags
- [ ] Progress tracking
- [ ] Notifications
- [ ] Mobile app (React Native)

---

**Last Updated**: January 19, 2026
**Version**: 1.0.0
