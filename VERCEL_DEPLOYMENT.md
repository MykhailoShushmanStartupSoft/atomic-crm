# Deploying Atomic CRM to Vercel

This guide will help you deploy your Atomic CRM application to Vercel.

## Prerequisites

1. **Vercel Account**: Sign up at [vercel.com](https://vercel.com)
2. **Vercel CLI**: Install globally with `npm install -g vercel`
3. **Git Repository**: Your code should be in a Git repository (GitHub, GitLab, or Bitbucket)

## Deployment Steps

### Option 1: Using Vercel CLI (Recommended)

1. **Navigate to your project directory**:
   ```bash
   cd test_react/atomic-crm
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up environment variables**:
   Create a `.env` file with your Supabase configuration:
   ```env
   VITE_SUPABASE_URL=your_supabase_url_here
   VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
   VITE_APP_TITLE=Atomic CRM
   VITE_APP_VERSION=0.0.2
   ```

4. **Deploy using the script**:
   ```bash
   npm run deploy:vercel
   ```

   Or manually:
   ```bash
   vercel --prod
   ```

### Option 2: Using Vercel Dashboard

1. **Push your code to GitHub/GitLab/Bitbucket**

2. **Connect your repository to Vercel**:
   - Go to [vercel.com/dashboard](https://vercel.com/dashboard)
   - Click "New Project"
   - Import your Git repository
   - Configure the following settings:
     - **Framework Preset**: Vite
     - **Build Command**: `npm run build`
     - **Output Directory**: `dist`
     - **Install Command**: `npm install`

3. **Add Environment Variables**:
   - In your Vercel project settings, go to "Environment Variables"
   - Add your Supabase configuration:
     - `VITE_SUPABASE_URL`
     - `VITE_SUPABASE_ANON_KEY`
     - `VITE_APP_TITLE`
     - `VITE_APP_VERSION`

4. **Deploy**:
   - Click "Deploy" and Vercel will automatically build and deploy your app

## Configuration Files

### vercel.json
This file configures the deployment:
- Sets the build command and output directory
- Configures SPA routing (all routes redirect to index.html)
- Sets up caching headers for static assets

### vite.config.ts
Updated to use absolute paths (`base: '/'`) for production deployment.

## Environment Variables

Make sure to set these environment variables in your Vercel project:

- `VITE_SUPABASE_URL`: Your Supabase project URL
- `VITE_SUPABASE_ANON_KEY`: Your Supabase anonymous key
- `VITE_APP_TITLE`: Application title
- `VITE_APP_VERSION`: Application version

## Troubleshooting

### Build Errors
- Ensure all dependencies are properly installed
- Check that TypeScript compilation passes locally
- Verify environment variables are set correctly

### Routing Issues
- The `vercel.json` file includes SPA routing configuration
- All routes should redirect to `index.html` for client-side routing

### Environment Variables
- Only variables prefixed with `VITE_` are available in the client-side code
- Set environment variables in Vercel dashboard under Project Settings > Environment Variables

## Post-Deployment

After successful deployment:
1. Your app will be available at `https://your-project-name.vercel.app`
2. Set up a custom domain if needed
3. Configure automatic deployments for future updates

## Continuous Deployment

Vercel automatically deploys when you push to your main branch. For other branches, it creates preview deployments.

## Support

- [Vercel Documentation](https://vercel.com/docs)
- [Vite Documentation](https://vitejs.dev/)
- [React Admin Documentation](https://marmelab.com/react-admin/)
